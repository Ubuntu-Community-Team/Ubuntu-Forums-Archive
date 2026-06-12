---
title: "problem getting internet connection"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by mielie007 on 2010-11-28
I'm having a problem getting my ubuntu machine to connect to the internet

I currently have a Ethernet network set up with a Netgear Firewall fvs114 and a PPPOE modem that.

A couple of months ago the my ubuntu machine stopped connecting to the internet. So I have been unable to upgrade over the internet. I have tried connecting the pppoe modem to the pc through the USB cable to see if I could connect to the internet through pppoe modem utility ubuntu comes with, but no luck.

I don't understand what has happened. I don't know if there is a setting that I have changed or not. I'm able to connect to the internet using my vista laptop through the network.

If there is anybody out there that has experienced this before and knows how to fix it please post a reply.

---

### Post by karthick87 on 2010-11-28
Are you using networkmanager for connecting to internet?

---

### Post by jerome_rajan on 2010-11-28
Are you dual booting your PC with Windows ? If yes, check if your parallel OS is properly shutdown or you have merely hibernated

PS : If you are using Gutsy Gibson, I'm sure you'll face a few hiccups. I was using Feist Fawn (7.04) & faced many problems.

---

### Post by jerome_rajan on 2010-11-28
Not sure if you followed these instructions. Took it from the Ubuntu documentation.

**Setting up PPPoE**

                                                                          To set up the modem:
                                    
[LIST=1]
[*]                       Open a terminal (Applications &#8594; Accessories &#8594; Terminal)
[*]                       In the terminal, type 
                       sudo pppoeconf
[*]                       A text-based menu program will guide you through the following steps: 					
                       
[LIST=1]
[*]                             Confirm that your Ethernet card is detected. 
[*]                             Enter your username. 
[*]                             Enter your password. 
[*]                             If you already have a PPPoE Connection configured, you will be asked if it may be modified. 
[*]                             Popular options: you are asked if you want the “noauth” and “defaultroute” options and to remove “nodetach”. Choose **Yes**. 
[*]                             Use peer DNS - choose **Yes**. 
[*]                             Limited MSS problem - choose **Yes**. 
[*]                             When you are asked if you want to connect at start up, you will probably want to say yes. 
[*]                             Finally you are asked if you want to establish the connection immediately. 
[/LIST]
                       
                     
[*]                       Once you have finished these steps, your connection should be working. 
[/LIST]
                 
                                                                                                              **Starting the connection**

                     
                   
                 
                 To start your ADSL connection on demand, in a terminal (Applications &#8594; Accessories &#8594; Terminal) type:
                 sudo pon dsl-provider               
                                                                                               **Stopping the connection**

                     
                   
                 
                 To stop your ADSL connection, in a terminal (Applications &#8594; Accessories &#8594; Terminal) type:
                 sudo poff dsl-provider

---

