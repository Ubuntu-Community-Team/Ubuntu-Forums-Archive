---
title: "LAN Connection on Lucid Lynx"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by CaronMargarete on 2010-10-10
> You will be connected to a wired network automatically when you plug in the      network cable.     
                    If you are not connected, your network may not have a DHCP service (DHCP is      responsible for assigning network settings). In this case, you will have to      manually enter your network settings.     
                                                                                               **Manually entering your network settings**

                     
                   
                 
                      	If you don't have DHCP on your network then you can configure a static      	connection. You will need to enter the network settings yourself, so      	check with your network administrator or look at your router's      	settings to find out which details to use.     	
                                    
[LIST=1]
[*]                            		    Right click the Network Manager icon in the system notification      		    area and click *Edit Connections*.     		    
[*]                            		    Click the *Wired* tab, select the connection      		    and click **Edit**.     		    
[*]                            		    Click the *IPv4 Settings* tab and choose      		    *Manual* from the      		    *Method* drop down list.     		    
[*]                            		    Click **Add** and enter your IP address and      		    other details. Enter the address of your DNS server too.     		    
[*]                            		    Click **Apply**. The network should now      		    connect if you entered the settings correctly.     		    
[/LIST]




I live in Cambodia and my internet provider knows zip about Ubuntu or what their DHCP client ID is, they can't even tell me what my IP address is but have managed to tell me my DNS server number.

I found my own IP: 115.178.27.24
The DNS they gave me is: 115.178.24.3

How do I find out what my netmask or gateway is so I can add the manual information? Or, simply get my laptop to recognise the LAN through the terminal?

Please help me with basic instructions.

---

### Post by Gone fishing on 2010-10-10
How are you connecting through a router? dialup? I would doubt - but might be wrong that you have a fixed IP.

How would you connect in Windows?

DHCP should work the same in either Ubuntu or Windows.

---

### Post by GabrielYYZ on 2010-10-10
if you use WICD network manager, DHCP should be automatic if you don't select a static IP.

---

### Post by CaronMargarete on 2010-10-10
> **Gone fishing said:**
> How are you connecting through a router? dialup? I would doubt - but might be wrong that you have a fixed IP.

How would you connect in Windows?

DHCP should work the same in either Ubuntu or Windows.

Broadband connection through Win7 normally connects through username and password to a modem not a router. 

It is possible that I don't have a fixed IP but I doubt it too. The IT guy at my service provider was confused by why I'd need the address and then told me that home users do not have IP addresses but the address I posted before has been one I've seen several times. So now I've no way to know because IT professionals here aren't incredibly proficient. 

Any way to use the terminal to suss it out?

---

### Post by CaronMargarete on 2010-10-10
> **GabrielYYZ said:**
> if you use WICD network manager, DHCP should be automatic if you don't select a static IP.

Ahhh correct me if I'm wrong but you need the Internet to download the WICD network manager and that's exactly what I don't have access to. I have to access Win7 just to post here.

---

### Post by Gone fishing on 2010-10-10
OK have you tried

Right click the networkmanager icon on the top panel select edit connections then select the DSL tab select add and follow the wizard.

Sorry if you've done this but lets start at the beginning

---

### Post by 3rdalbum on 2010-10-10
Do not choose "Manual" under the IPv4 settings. Choose "Automatic (Addresses Only)" and then you only need to specify the DNS setting. The IP address you found is an external address, not an internal one, so it's probably not what your computer can work with.

---

### Post by CaronMargarete on 2010-10-10
> **Gone fishing said:**
> OK have you tried

Right click the networkmanager icon on the top panel select edit connections then select the DSL tab select add and follow the wizard.

Sorry if you've done this but lets start at the beginning
 
Tried. No love.

---

### Post by CaronMargarete on 2010-10-10
> **3rdalbum said:**
> Do not choose "Manual" under the IPv4 settings. Choose "Automatic (Addresses Only)" and then you only need to specify the DNS setting. The IP address you found is an external address, not an internal one, so it's probably not what your computer can work with.

Tried this too. No love.

---

### Post by Gone fishing on 2010-10-10
OK here's a commandline way 

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

However, before you do do you have all the settings need just check on a working windows box as network manager should work.

---

### Post by CaronMargarete on 2010-10-10
> **Gone fishing said:**
> OK here's a commandline way 

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

However, before you do do you have all the settings need just check on a working windows box as network manager should work.

Thanks for the link, however, your message isn't very clear. Yes it works for Win7 (separate partition) and I assume wifi would work, although I haven't tried since I recently went through [problems with Win7 overwriting my MBR]("http://ubuntuforums.org/showthread.php?p=9946631#post9946631"), I have it sorted out now but could it impact on the Internet connection now?

I didn't use LAN before the Win7 problem so I have no idea if this problem has always existed or if it's new.

Will wait for your reply before attempting the link.

---

### Post by Gone fishing on 2010-10-10
Sorry I meant if you have the PPPoE working with another box or Windows we could just check all the settings username, password provider, IP address or DHCP etc,etc

Just to check there is no silly mistake when using network manager before going for the command line solution

---

### Post by Gone fishing on 2010-10-10
Your in Colombia? Sorry my Spanish is not too good but is the an Ubuntu event near you next week where I'm sure you could meet some experienced Ubuntu users 

[http://ubuntu-co.com/](http://ubuntu-co.com/)

Ooops sorry Cambodia not Colombia

---

### Post by cap10Ibraim on 2010-10-10
> **CaronMargarete said:**
> I live in Cambodia and my internet provider knows zip about Ubuntu or what their DHCP client ID is, they can't even tell me what my IP address is but have managed to tell me my DNS server number.

I found my own IP: 115.178.27.24
The DNS they gave me is: 115.178.24.3

How do I find out what my netmask or gateway is so I can add the manual information? Or, simply get my laptop to recognise the LAN through the terminal?

Please help me with basic instructions.

this is a public ip so I doubt it's yours 
how did you find it ? from a website ? 
I guess this IP belongs to the ISP 
still guessing you have your private IP on the ISP LAN 
but they use this external IP to get you to the internet (similar to natting stuff)

---

### Post by dineshs on 2010-10-11
> **Gone fishing said:**
> OK have you tried

Right click the networkmanager icon on the top panel select edit connections then select the DSL tab select add and follow the wizard.

Sorry if you've done this but lets start at the beginning
I think this is the right way.A detailed explanation is [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
Also please post the result of
```
sudo lshw -C network
```

---

### Post by CaronMargarete on 2010-10-13
> **Gone fishing said:**
> OK here's a command line way 

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

However, before you do do you have all the settings need just check on a working windows box as network manager should work.

Turns out that the internet provider had a representative that knew about Ubuntu and walked me through this process. Worked a charm.

Thanks for your help and guidance.

---

