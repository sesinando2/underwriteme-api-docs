## List [/application/{applicationId}/comparison]
Operations on existing Comparison associated with Application.

In order to get quote values for the Comparison PUT method has to be used to request it. Quoting is done in asynchronous way which means that values may not come back straight away. Use GET method to query the comparison for updated quote state.

Any expired quotes will be requoted when Comparison is requested with PUT method. In order to check whether quotes have expired, first use the GET method to retrieve the Comparison.

Until all Enquiries are closed Comparison contains only estimated decisions and quotes.

JSON response has following structure:

- _**estimated**_ `boolean` *(optional)* - Flag stating that all decisions and quotes are estimated. This flag is shown in the response if enquiries are not closed.
- _**items**_ `array` *(required)* - List of Comparison Items (represented as `object` type) containing decision, quote and other Provider specific details for particular Product. Detailed structure of Comparison Item can be found in the following Comparison / Item section.
- _**quickQuotes**_ `array` *(required)* - List of Quick Quote Items (represented as `object` type) containing decision, quote and other Provider specific details for particular Product. Detailed structure of Comparison Item can be found in the following Comparison / Item section. Note quick quote items should not be treated as standard Comparison Items.

+ Parameters

    + applicationId (required, string, `1502181407123020689`) ... Unique ID of existing Application.

### Request Comparison [PUT]
+ Request Comparison with pending, succeeded, failed and no quotes. (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "estimated":true,
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"UNKNOWN",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quotable": true,
                        "quote":{
                            "state":"PENDING"
                        },
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"UNKNOWN",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": true,
                        "quotable": true,
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-01-01T00:00:00.000",
                            "expiryDate":"2015-02-01",
                            "premium":{
                                "from":9.84,
                                "to":9.84,
                                "lifetime":1180.80,
                                "lives":[
                                    {
                                        "refersTo":"4083"
                                    }
                                ],
                                "discount": 0.00
                            },
                            "notes": [
                              {
                                "description": "description1",
                                "reason": "note1",
                                "important": false
                              },
                              {
                                "description": "description2",
                                "reason": "note2",
                                "important": false
                              }
                            ],
                            "variations": [
                              {
                                "originalValue": "originalValue1",
                                "newValue": "newValue1",
                                "reason": "reason1"
                              },
                              {
                                "originalValue": "originalValue2",
                                "newValue": "newValue2",
                                "reason": "reason2"
                              }
                            ],                            
                            "sumAssured":120000,
                            "commission":{
                                "initial":30.61,
                                "renewal":8.17,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerY",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"DECLINE",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"DECLINE",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "message":"Unfortunately InsurerY is unable to provide you with Life Insurance"
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quotable": true,
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurery.com/term/key-facts.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"insurery-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerZ",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"NON_STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"NON_STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quotable": true,
                        "quote":{
                            "state":"FAILED"
                        },
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerz.com/term/key-facts.pdf"
                        },
                        "id":"insurerz-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ]
            }

### Retrieve Comparison [GET]
+ Request Estimated Comparison with unknown decisions for new Application. (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "estimated":true,
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"UNKNOWN",
                            "immediateCover":false,
                            "nonIndicative":true,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quotable": true,
                        "quote":{
                            "state":"PENDING"
                        },
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4083"
                                }
                            ]
                        },
                        "decision":{
                            "type":"UNKNOWN",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4083",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quotable": true,
                        "quote":{
                            "state":"PENDING"
                        },
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ],
                 "quickQuotes" :[
                     {
                         "provider":"InsurerA",
                         "product":{
                             "id":"fsdsfsd-1ads-3w12-au1z-223d0f1cbb61",
                             "referenceId":"pro-001",
                             "type":"TERM",
                             "coverBasis":"DECREASING",
                             "coverPeriod":10,
                             "coverAmount":200000,
                             "livesAssured":[
                                 {
                                     "name":"Jane",
                                     "surname":"Doe",
                                     "refersTo":"4083"
                                 }
                             ]
                         },
                         "decision":{
                             "type":"UNKNOWN",
                             "immediateCover":true,
                             "nonIndicative":false,
                             "details":[
                                 {
                                     "customer":{
                                         "id":"4083",
                                         "name":"Jane",
                                         "surname":"Doe"
                                     },
                                     "decisions":[
                                         {
                                             "type":"UNKNOWN",
                                             "componentType":"LIFE",
                                             "optional":false
                                         }
                                     ]
                                 }
                             ]
                         },
                         "purchasable": false,
                         "quotable": true,
                         "quote":{
                             "state":"PENDING"
                         },
                         "rating":{
                             "value":5,
                             "description":"<strong>Recommended</strong>"
                         },
                         "details":{
                             "keyFacts":"http://plr.com/term/key-facts.pdf",
                             "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                             "shortDescription":"Some more information about this term product"
                         },
                         "id":"plr-fsdsfsd-1ads-3w12-au1z-223d0f1cbb61"
                     }
                 ]
            }

+ Request Estimated Comparison with referred decisions for not-satisfied Enquiry (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "estimated":true,
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4084",
                                    "waiverOfPremium":true
                                }
                            ]
                        },
                        "decision":{
                            "type":"REFER",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4084",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Family History Parkinsons Disease",
                                                        "triggerTag":"Family History Parkinsons Disease",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "sum":50
                                                    }
                                                }
                                            ]
                                        },
                                        {
                                            "type":"REFER",
                                            "componentType":"WOP",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "indicativeExclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Family History Parkinsons Disease",
                                                        "triggerTag":"Family History Parkinsons Disease",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXPAR",
                                                            "description":"No benefit will be payable under this policy for any claims arising from Parkinson's disease or any other form of movement disorder or degenerative disorder"
                                                        }
                                                    ]
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": true,
                        "quotable": true,
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-08-13T10:45:31.000",
                            "premium":{
                                "from":45.44,
                                "to":45.44,
                                "unloaded":{
                                    "from":45.44,
                                    "to":45.44
                                },
                                "lifetime":5452.85,
                                "lives":[
                                    {
                                        "refersTo":"4084",
                                        "wopContribution":1.02
                                    }
                                ],
                                "discount": 0.00
                            },
                            "sumAssured":110000,
                            "commission":{
                                "initial":959.25,
                                "renewal":1.14,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4084",
                                    "waiverOfPremium":true
                                }
                            ]
                        },
                        "decision":{
                            "type":"REFER",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4084",
                                        "name":"John",
                                        "surname":"Doe",
                                        "waiverOfPremium":true
                                    },
                                    "decisions":[
                                        {
                                            "type":"REFER",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Family History Parkinsons Disease",
                                                        "triggerTag":"Family History Parkinsons Disease",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "sum":50
                                                    }
                                                }
                                            ],
                                            "indicativePermilleContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Suicide",
                                                        "triggerTag":"Suicide attempt",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "from":5,
                                                        "to":5
                                                    }
                                                }
                                            ],
                                            "evidenceContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Suicide",
                                                        "triggerTag":"Suicide attempt",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"TGPR",
                                                            "description":"Targeted GP Report"
                                                        }
                                                    ]
                                                }
                                            ]
                                        },
                                        {
                                            "type":"REFER",
                                            "componentType":"WOP",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "indicativeExclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Family History Parkinsons Disease",
                                                        "triggerTag":"Family History Parkinsons Disease",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXPAR",
                                                            "description":"No benefit will be payable under this policy for any claims arising from Parkinson's disease or any other form of movement disorder or degenerative disorder"
                                                        }
                                                    ]
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "purchasable": false,
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ],
                "quickQuotes": []
            }

+ Request Estimated Comparison with standard decisions for satisfied Enquiry (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "estimated":true,
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4085"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4085",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "duration":"P3Y",
                                                        "sum":2
                                                    }
                                                }
                                            ],
                                            "permilleContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "duration":"P1Y",
                                                        "sum":1
                                                    }
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4085"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4085",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "sum":2
                                                    }
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quotable": true,
                        "quote":{
                            "state":"PENDING"
                        },
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ],
                "quickQuotes": []
            }

+ Request Valid Comparison with standard decisions for satisfied and closed Enquiry (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"CRITICAL_ILLNESS_WITH_LIFE_COVER",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "premiumBasis":"GUARANTEED",
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4086",
                                    "waiverOfPremium":true
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4086",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"WOP",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXEYE",
                                                            "description":"No benefit will be payable under this policy for any claims arising from any disease or disorder of the eye including blindness"
                                                        }
                                                    ]
                                                }
                                            ]
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"TPD",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXEYE",
                                                            "description":"No benefit will be payable under this policy for any claims arising from any disease or disorder of the eye including blindness"
                                                        }
                                                    ]
                                                }
                                            ]
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"CI",
                                            "optional":false,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"CIRMBLI",
                                                            "description":"Blindness is removed as an insured condition"
                                                        }
                                                    ]
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/ci/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/ci/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"CRITICAL_ILLNESS_WITH_LIFE_COVER",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "premiumBasis":"GUARANTEED",
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4086",
                                    "waiverOfPremium":true
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4086",
                                        "name":"John",
                                        "surname":"Doe",
                                        "waiverOfPremium":true
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"WOP",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXEYE",
                                                            "description":"No benefit will be payable under this policy for any claims arising from any disease or disorder of the eye including blindness"
                                                        }
                                                    ]
                                                }
                                            ]
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"TPD",
                                            "disabilityDefinition":"Own Occupation",
                                            "optional":true,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"EXEYE",
                                                            "description":"No benefit will be payable under this policy for any claims arising from any disease or disorder of the eye including blindness"
                                                        }
                                                    ]
                                                }
                                            ]
                                        },
                                        {
                                            "type":"STANDARD",
                                            "componentType":"CI",
                                            "optional":false,
                                            "exclusionContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Detached Retina",
                                                        "triggerTag":"Blindness in one eye",
                                                        "derived": false
                                                    },
                                                    "value":[
                                                        {
                                                            "code":"CIRMBLI",
                                                            "description":"Blindness is removed as an insured condition"
                                                        }
                                                    ]
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/ci/key-facts.pdf"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ],
                "quickQuotes": []
            }

+ Request Valid Comparison for 2 Products with refer and decline decisions. (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "items":[
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"acf83c43-2079-4b5e-a6f9-2a9421536cc4",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4088"
                                }
                            ]
                        },
                        "decision":{
                            "type":"REFER",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4088",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"REFER",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf"
                        },
                        "id":"insurerx-acf83c43-2079-4b5e-a6f9-2a9421536cc4"
                    },
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"acf83c43-2079-4b5e-a6f9-2a9421536cc4",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4088"
                                }
                            ]
                        },
                        "decision":{
                            "type":"REFER",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4088",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"REFER",
                                            "componentType":"LIFE",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"PENDING"
                        },
                        "quotable": true,
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-acf83c43-2079-4b5e-a6f9-2a9421536cc4"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"7044b1fa-6fb5-46fb-b8fc-d785cac42112",
                            "referenceId":"pro-001",
                            "type":"CRITICAL_ILLNESS_WITH_LIFE_COVER",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "premiumBasis":"GUARANTEED",
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4088"
                                }
                            ]
                        },
                        "decision":{
                            "type":"DECLINE",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4088",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"REFER",
                                            "componentType":"LIFE",
                                            "optional":false
                                        },
                                        {
                                            "type":"DECLINE",
                                            "componentType":"CI",
                                            "optional":false,
                                            "message":"Unfortunately InsurerX is unable to provide you with Life Insurance"
                                        },
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"CI_DECREASING",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "quotable": false,
                        "id":"insurerx-7044b1fa-6fb5-46fb-b8fc-d785cac42112"
                    },
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"7044b1fa-6fb5-46fb-b8fc-d785cac42112",
                            "referenceId":"pro-001",
                            "type":"CRITICAL_ILLNESS_WITH_LIFE_COVER",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "premiumBasis":"GUARANTEED",
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4088"
                                }
                            ]
                        },
                        "decision":{
                            "type":"DECLINE",
                            "immediateCover":false,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4088",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"REFER",
                                            "componentType":"LIFE",
                                            "optional":false
                                        },
                                        {
                                            "type":"DECLINE",
                                            "componentType":"CI",
                                            "optional":false,
                                            "message":"Unfortunately PLR is unable to provide you with Life Insurance"
                                        },
                                        {
                                            "type":"UNKNOWN",
                                            "componentType":"CI_DECREASING",
                                            "optional":false
                                        }
                                    ]
                                }
                            ]
                        },
                        "quotable": false,
                        "id":"plr-7044b1fa-6fb5-46fb-b8fc-d785cac42112"
                    }
                ],
                "quickQuotes": []
            }

+ Request Comparison for an IP product. (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "items":[
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"153a6779-cf28-4d9e-a906-91594652c939",
                            "type":"INCOME_PROTECTION",
                            "coverBasis":"LEVEL",
                            "coverUntilAge":51,
                            "coverAmount":1000,
                            "deferredPeriodInWeeks":4,
                            "premiumBasis":"GUARANTEED",
                            "commissionSacrifice":{
                                "initial":0,
                                "renewal":2.50, 
                                "nilBased": false
                            },
                            "extendedCoverType":"FULL",
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"527"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "details":[
                                {
                                    "customer":{
                                        "id":"527",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"IP_4",
                                            "optional":false,
                                            "disabilityDefinition":"Own Occupation"
                                        }
                                    ]
                                }
                            ],
                            "immediateCover":true,
                            "nonIndicative":false
                        },
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-08-13T10:45:31.000",
                            "premium":{
                                "from":45.44,
                                "to":45.44,
                                "unloaded":{
                                    "from":45.44,
                                    "to":45.44
                                },
                                "lifetime":5452.85,
                                "lives":[
                                    {
                                        "refersTo":"527"
                                    }
                                ],
                                "discount": 0.00
                            },
                            "sumAssured":1000,
                            "anonymousQuote":false,
                            "commission":{
                                "initial":959.25,
                                "renewal":1.14,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "quotable": true,
                        "id":"insurerx-153a6779-cf28-4d9e-a906-91594652c939"
                    },
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"153a6779-cf28-4d9e-a906-91594652c939",
                            "type":"INCOME_PROTECTION",
                            "coverBasis":"LEVEL",
                            "coverUntilAge":51,
                            "coverAmount":1000,
                            "deferredPeriodInWeeks":4,
                            "premiumBasis":"GUARANTEED",
                            "commissionSacrifice":{
                                "initial":0,
                                "renewal":2.50, 
                                "nilBased": false
                            },
                            "extendedCoverType":"FULL",
                                 "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"527"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "details":[
                                {
                                    "customer":{
                                        "id":"527",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"IP_4",
                                            "optional":false,
                                            "disabilityDefinition":"Own Occupation"
                                        }
                                    ]
                                }
                            ],
                            "immediateCover":true,
                            "nonIndicative":false
                        },
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-08-13T10:45:31.000",
                            "premium":{
                                "from":53.86,
                                "to":53.86,
                                "unloaded":{
                                    "from":53.86,
                                    "to":53.86
                                },
                                "lifetime":6463.50,
                                "lives":[
                                    {
                                        "refersTo":"527"
                                    }
                                ],
                                "discount": 0.00
                            },
                            "sumAssured":1000,
                            "anonymousQuote":false,
                            "commission":{
                                "initial":1137.04,
                                "renewal":1.35,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "quotable": true,
                        "id":"plr-153a6779-cf28-4d9e-a906-91594652c939"
                    }
                ],
                "quickQuotes": []
            }

+ Request Comparison containing an expired item (application/json)

    + Headers

            Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1c2VybmFtZSIsImV4cCI6MTQyMjU0MDAzMH0.oyMYL7t57jhBvw-A3vghOAXl6cixpaTsZW69wz3p5M8

+ Response 200

            {
                "estimated":true,
                "items":[
                    {
                        "provider":"PLR",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4085"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4085",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "duration":"P3Y",
                                                        "sum":2
                                                    }
                                                }
                                            ],
                                            "permilleContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "duration":"P1Y",
                                                        "sum":1
                                                    }
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-01-01T00:00:00.000",
                            "expiryDate":"2014-02-01",
                            "expired":true,
                            "premium":{
                                "from":9.84,
                                "to":9.84,
                                "lifetime":1180.80,
                                "lives":[
                                    {
                                        "refersTo":"4085"
                                    }
                                ],
                                "discount": 0.00
                            },
                            "sumAssured":120000,
                            "anonymousQuote":false,
                            "commission":{
                                "initial":30.61,
                                "renewal":8.17,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "quotable": true,
                        "rating":{
                            "value":5,
                            "description":"<strong>Recommended</strong>"
                        },
                        "details":{
                            "keyFacts":"http://plr.com/term/key-facts.pdf",
                            "termsAndConditions":"http://plr.com/term/terms-and-conditions.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"plr-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    },
                    {
                        "provider":"InsurerX",
                        "product":{
                            "id":"ac33ac4f-5aea-4a49-af1a-817d0d1cbf80",
                            "referenceId":"pro-001",
                            "type":"TERM",
                            "coverBasis":"DECREASING",
                            "coverPeriod":10,
                            "coverAmount":110000,
                            "livesAssured":[
                                {
                                    "name":"John",
                                    "surname":"Doe",
                                    "refersTo":"4085"
                                }
                            ]
                        },
                        "decision":{
                            "type":"STANDARD",
                            "immediateCover":true,
                            "nonIndicative":false,
                            "details":[
                                {
                                    "customer":{
                                        "id":"4085",
                                        "name":"John",
                                        "surname":"Doe"
                                    },
                                    "decisions":[
                                        {
                                            "type":"STANDARD",
                                            "componentType":"LIFE",
                                            "optional":false,
                                            "extraMorbidityContributions":[
                                                {
                                                    "contributor":{
                                                        "enquiryLine":"Arthritis",
                                                        "triggerTag":"Arthritis",
                                                        "derived": false
                                                    },
                                                    "value":{
                                                        "sum":2
                                                    }
                                                }
                                            ]
                                        }
                                    ]
                                }
                            ]
                        },
                        "quote":{
                            "state":"SUCCEEDED",
                            "date":"2015-01-01T00:00:00.000",
                            "expiryDate":"2015-02-01",
                            "premium":{
                                "from":9.84,
                                "to":9.84,
                                "lifetime":1180.80,
                                "lives":[
                                    {
                                        "refersTo":"4085"
                                    }
                                ],
                                "discount": 0.00
                            },
                            "sumAssured":120000,
                            "anonymousQuote":false,
                            "commission":{
                                "initial":30.61,
                                "renewal":8.17,
                                "sacrifice":{
                                    "initial":0,
                                    "renewal":2.50
                                }
                            }
                        },
                        "quotable": true,
                        "rating":{
                            "value":4,
                            "description":"Good"
                        },
                        "details":{
                            "keyFacts":"http://insurerx.com/term/key-facts.pdf",
                            "shortDescription":"Some more information about this term product"
                        },
                        "id":"insurerx-ac33ac4f-5aea-4a49-af1a-817d0d1cbf80"
                    }
                ],
                "quickQuotes": []
            }
