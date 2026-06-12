---
title: "Thinkpad can't connect to some open AP's"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by fivebells on 2008-08-18
Hi.  I have a thinkpad running Hardy Heron.  The iwl3945 module is installed.  There is an open AP at work which it connects to without difficulty.  However, it has problems with the open AP at home.  I have an old iBook which connects to the home AP without problems.  According to iwconfig, the thinkpad is binding to the correct ESSID, but the syslog contains the following messages.  I have summarized and elided some lines which I hope to be unimportant, as I am transferring it to a computer with working network via FingerNet:

RX deauthentication from <AP MAC address> (reason=7) (this repeats about 20 times.)                                                                      
nm_device_802_11_wireless_get_activation_ap(): Forcing AP <AP ESSID>                                                                                     
RX deauthentication from <AP MAC address> (reason=7) (this repeats about 20 times.)                                                                      
Initial auth_alg=0                                                                                                                                       
authenticate with AP <AP MAC address>                                                                                                                    
RX deauthentication from <AP MAC address> (reason=7)                                                                                                     
Initial auth_alg=0                                                                                                                                       
authenticate with AP <AP MAC address>                                                                                                                    
RX authentication from <AP MAC address> (alg=0 transaction=2 status=0)                                                                                   
authenticated                                                                                                                                            
associate with AP <AP MAC address>                                                                                                                       
RX AssocResp from <AP MAC address> (capab=0x601 status=18 aid=1)                                                                                         
AP denied association (code=18)                                                                                                                          
association with AP <AP MAC address> timed out                                                                                                           
                                                                                                                                                         
This sequence repeats a few times until the Network Manager gives up.                                                                                    
                                                                        
I asked some friends about this.  One of them said that it looks like it's trying to do WPA authentication.  Apparently sometimes the iwl3945 module keeps trying to use WPA authentication when the laptop moves to a different AP.  According to "iwlist scan", the AP is unencrypted.  My friend suggested reloading the module, but this did not change the behavior.

I'd really appreciate some insight into this, as I am stuck.

---

