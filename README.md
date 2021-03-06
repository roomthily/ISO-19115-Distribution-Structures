#How many valid representations can an ISO 19115 (MI/MD) record have?


Starting point for each: minimum_valid_document.xml

Note: I will not be including all empty element structures. That's just padding the result set :/.

Example 1. No distribution.

```
<gmd:distributionInfo/>
```

Example 2. A single link in transferOptions 

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:transferOptions>
            <gmd:MD_DigitalTransferOptions>
                <gmd:onLine>
                    <gmd:CI_OnlineResource>
                        <gmd:linkage>
                            <gmd:URL>www.my_url.com</gmd:URL>
                        </gmd:linkage>
                    </gmd:CI_OnlineResource>
                </gmd:onLine>
            </gmd:MD_DigitalTransferOptions>
        </gmd:transferOptions>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 3. A single link with transfer size

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:transferOptions>
            <gmd:MD_DigitalTransferOptions>
                <gmd:transferSize>
                    <gco:Real>10.0</gco:Real>
                </gmd:transferSize>
                <gmd:onLine>
                    <gmd:CI_OnlineResource>
                        <gmd:linkage>
                            <gmd:URL>www.my_url.com</gmd:URL>
                        </gmd:linkage>
                    </gmd:CI_OnlineResource>
                </gmd:onLine>
            </gmd:MD_DigitalTransferOptions>
        </gmd:transferOptions>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 4. A basic distributionFormat block

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:distributionFormat>
            <gmd:MD_Format>
                <gmd:name>
                    <gco:CharacterString>A Format</gco:CharacterString>
                </gmd:name>
                <gmd:version>
                    <gco:CharacterString>1.0</gco:CharacterString>
                </gmd:version>
            </gmd:MD_Format>
        </gmd:distributionFormat>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 5. A distribution format with a format distributor (context matters but we'll just consider any URL endpoint here).

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:distributionFormat>
            <gmd:MD_Format>
                <gmd:name>
                    <gco:CharacterString>A Format</gco:CharacterString>
                </gmd:name>
                <gmd:version>
                    <gco:CharacterString>1.0</gco:CharacterString>
                </gmd:version>
                <gmd:formatDistributor>
                    <gmd:MD_Distributor>
                        <gmd:distributorContact/>
                        <gmd:distributorTransferOptions>
                            <gmd:MD_DigitalTransferOptions>
                                <gmd:onLine>
                                    <gmd:CI_OnlineResource>
                                        <gmd:linkage>
                                            <gmd:URL>www.my_url.com</gmd:URL>
                                        </gmd:linkage>
                                    </gmd:CI_OnlineResource>
                                </gmd:onLine>
                            </gmd:MD_DigitalTransferOptions>
                        </gmd:distributorTransferOptions>
                    </gmd:MD_Distributor>
                </gmd:formatDistributor>
            </gmd:MD_Format>
        </gmd:distributionFormat>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 6. Basic distributor (seeing a pattern here)

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:distributor>
            <gmd:MD_Distributor>
                <gmd:distributorContact/>
                <gmd:distributorTransferOptions>
                    <gmd:MD_DigitalTransferOptions>
                        <gmd:onLine>
                            <gmd:CI_OnlineResource>
                                <gmd:linkage>
                                    <gmd:URL>www.my_url.com</gmd:URL>
                                </gmd:linkage>
                            </gmd:CI_OnlineResource>
                        </gmd:onLine>
                    </gmd:MD_DigitalTransferOptions>
                </gmd:distributorTransferOptions>
            </gmd:MD_Distributor>
        </gmd:distributor>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 7. That really shouldn't be okay.

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:distributor>
            <gmd:MD_Distributor>
                <gmd:distributorContact/>
                <gmd:distributorFormat>
                    <gmd:MD_Format>
                        <gmd:name/>
                        <gmd:version/>
                        <gmd:formatDistributor>
                            <gmd:MD_Distributor>
                                <gmd:distributorContact/>
                                <gmd:distributorTransferOptions>
                                    <gmd:MD_DigitalTransferOptions>
                                        <gmd:onLine>
                                            <gmd:CI_OnlineResource>
                                                <gmd:linkage>
                                                    <gmd:URL>www.my_url.com</gmd:URL>
                                                </gmd:linkage>
                                            </gmd:CI_OnlineResource>
                                        </gmd:onLine>
                                    </gmd:MD_DigitalTransferOptions>
                                </gmd:distributorTransferOptions>
                            </gmd:MD_Distributor>
                        </gmd:formatDistributor>
                    </gmd:MD_Format>
                </gmd:distributorFormat>
            </gmd:MD_Distributor>
        </gmd:distributor>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 8. At some point, the codelists need to come into play.

```
<gmd:distributionInfo>
    <gmd:MD_Distribution>
        <gmd:distributor>
            <gmd:MD_Distributor>
                <gmd:distributorContact/>
                <gmd:distributorFormat>
                    <gmd:MD_Format>
                        <gmd:name></gmd:name>
                        <gmd:version></gmd:version>
                        <gmd:formatDistributor>
                            <gmd:MD_Distributor>
                                <gmd:distributorContact/>
                                <gmd:distributorTransferOptions>
                                    <gmd:MD_DigitalTransferOptions>
                                        <gmd:onLine>
                                            <gmd:CI_OnlineResource>
                                                <gmd:linkage>
                                                    <gmd:URL>www.my_url.com</gmd:URL>
                                                </gmd:linkage>
                                            </gmd:CI_OnlineResource>
                                        </gmd:onLine>
                                    </gmd:MD_DigitalTransferOptions>
                                </gmd:distributorTransferOptions>
                            </gmd:MD_Distributor>
                        </gmd:formatDistributor>
                    </gmd:MD_Format>
                </gmd:distributorFormat>
                <gmd:distributorTransferOptions>
                    <gmd:MD_DigitalTransferOptions>
                        <gmd:onLine>
                            <gmd:CI_OnlineResource>
                                <gmd:linkage>
                                    <gmd:URL>www.my_url.com</gmd:URL>
                                </gmd:linkage>
                            </gmd:CI_OnlineResource>
                        </gmd:onLine>
                    </gmd:MD_DigitalTransferOptions>
                </gmd:distributorTransferOptions>
            </gmd:MD_Distributor>
        </gmd:distributor>
    </gmd:MD_Distribution>
</gmd:distributionInfo>
```

Example 9. Moving on to Service Metadata. Remember the pattern?

```
<gmd:identificationInfo>
    <gmd:MD_ServiceIdentification>
        <gmd:citation/>
        <gmd:abstract/>
        <gmd:resourceFormat>
            <gmd:MD_Format>
                <gmd:name/>
                <gmd:version/>
                <gmd:formatDistributor>
                    <gmd:MD_Distributor>
                        <gmd:distributorContact/>
                        <gmd:distributorTransferOptions>
                            <gmd:MD_DigitalTransferOptions>
                                <gmd:onLine>
                                    <gmd:CI_OnlineResource>
                                        <gmd:linkage>
                                            <gmd:URL>www.my_url.com</gmd:URL>
                                        </gmd:linkage>
                                    </gmd:CI_OnlineResource>
                                </gmd:onLine>
                            </gmd:MD_DigitalTransferOptions>
                        </gmd:distributorTransferOptions>
                    </gmd:MD_Distributor>
                </gmd:formatDistributor>
            </gmd:MD_Format>
        </gmd:resourceFormat>
    </gmd:MD_ServiceIdentification>
</gmd:identificationInfo>
```

Example 10. Proper service identification.

```
<gmd:identificationInfo>
    <srv:SV_ServiceIdentification>
        <gmd:citation/>
        <gmd:abstract/>
        <srv:serviceType/>
        <srv:couplingType/>
        <srv:containsOperations>
            <srv:SV_OperationMetadata>
                <srv:operationName/>
                <srv:DCP/>
                <srv:connectPoint>
                    <gmd:CI_OnlineResource>
                        <gmd:linkage>
                            <gmd:URL>www.my_url.com</gmd:URL>
                        </gmd:linkage>
                    </gmd:CI_OnlineResource>
                </srv:connectPoint>
            </srv:SV_OperationMetadata>
        </srv:containsOperations>
    </srv:SV_ServiceIdentification>
</gmd:identificationInfo>
```

And there it is. Looks like just the ten. I am a little disappointed, but, really, some of the difference is related to elements not included here. 



