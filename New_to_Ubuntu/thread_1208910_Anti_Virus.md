---
title: "Anti Virus"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by cazzz on 2009-07-09
Hi i am a newbie to Linux and enjoy using the system I just need to know a few things

I have installed Ubuntu on Sun Virtual machine 

My main operating system is Vista and on Vista I have Installed Avira Anti virus and SuperAnti Spyware and Malware Bytes  

I have no Anti Virus Or Anti Spyware on Ubuntu Running in the Sun Virtual Machince

Do I need to install a Anti Virus And anti Spyware in Ubuntu As Well As my Vista I have read on a forum This will only been needed if the Connection is bridged i am a total newbie and do not understand what bridge connection is or if i even do have Ubuntu Bridged Connected? Will you please be kind Enough to explain this to me and if i need to install anti virus and anti spyware in Ubuntu and instruction on how i could achieve this 

Thankyou in Advance to any replys i get for this problem

---

### Post by Viva on 2009-07-09
You don't need an antivirus on ubuntu. The existing antivirus software only check for windows viruses.

---

### Post by scrooge_74 on 2009-07-09
Linux in general dosent need antivirus, firewall is already up and running no need to do anything

---

### Post by binbash on 2009-07-09
You do not need any antivirus software on Ubuntu unless you are planning to scan your Windows folders.

---

### Post by cazzz on 2009-07-09
Guys can you explain a bit more in death please

[COLOR=Red]QUOTE FROM HELPERS[/COLOR] Existing software only checks for windows virus ??[COLOR=Red]QUOTE FROM HELPERS[/COLOR]

 IF this is the case So which software will Check For the Linux Ubuntu Virus If Linux Get Infected? In the virtual machine and spreads to my vista Operating system????


[COLOR=Red]QUOTE FROM HELPERS [/COLOR]Linux in general dosent need antivirus, firewall is already up and running no need to do anything [COLOR=Red]QUOTE FROM HELPERS[/COLOR]

Why does Ubuntu Not need a antivirus??? And which firewall wall is up and running does it have already built in? Is The firewall IN ubuntu Conflicting the one on my vista?? and again what if ubuntu gets infected and spreads to Vista Operating system


[COLOR=Red]QUOTE FROM HELPERS[/COLOR] You do not need any antivirus software on Ubuntu unless you are planning to scan your Windows folders. [COLOR=Red]QUOTE FROM HELPERS[/COLOR]

Please can you expain a bit more in detail I have already anti virus and anti spyware on vista Will this not scan the folders



Also Guys I have heard if you get infected in Ubuntu And have a bridge network Then it will Infect the other Operating system On the partition Too?

Thankyou in advance

---

### Post by Viva on 2009-07-09
All the existing linux viruses have been fixed long ago. None of the existing viruses will work on your ubuntu. New security vulnerabilities are fixed quickly, so just make sure you update your ubuntu system regularly.

---

### Post by cazzz on 2009-07-09
> **Viva said:**
> All the existing linux viruses have been fixed long ago. None of the existing viruses will work on your ubuntu. New security vulnerabilities are fixed quickly, so just make sure you update your ubuntu system regularly.


Viva Are you saying to me Ubuntu Can not infect My vista at all? No way it will Pass Virus To my vista Folders??? I am running Ubutu AS guest and Vista as my main host

---

### Post by doas777 on 2009-07-09
> **cazzz said:**
> Guys can you explain a bit more in death please

[COLOR=Red]QUOTE FROM HELPERS[/COLOR] Existing software only checks for windows virus ??[COLOR=Red]QUOTE FROM HELPERS[/COLOR]

 IF this is the case So which software will Check For the Linux Ubuntu Virus If Linux Get Infected? In the virtual machine and spreads to my vista Operating system????


[COLOR=Red]QUOTE FROM HELPERS [/COLOR]Linux in general dosent need antivirus, firewall is already up and running no need to do anything [COLOR=Red]QUOTE FROM HELPERS[/COLOR]

Why does Ubuntu Not need a antivirus??? And which firewall wall is up and running does it have already built in? Is The firewall IN ubuntu Conflicting the one on my vista?? and again what if ubuntu gets infected and spreads to Vista Operating system


[COLOR=Red]QUOTE FROM HELPERS[/COLOR] You do not need any antivirus software on Ubuntu unless you are planning to scan your Windows folders. [COLOR=Red]QUOTE FROM HELPERS[/COLOR]

Please can you expain a bit more in detail I have already anti virus and anti spyware on vista Will this not scan the folders



Also Guys I have heard if you get infected in Ubuntu And have a bridge network Then it will Infect the other Operating system On the partition Too?

Thankyou in advance

1) there are no linux viruses. there used to be some worms (and there will be again in the future), and most spyware that works in firefox will work on ubuntu as well as it will in windows. bleachbit is good for cleaning the ff cache. rootkits are also a problem but you prettty much need to be tricked into installing them with root. you can find most f them with rkhunter and chkrootkit. instead of worrying about the rootkit itself, lock down your system so that no one can get root except you, so noone can install one.

No virus ever created can affect a vm host (except mabey the theoretical blue pill). only the guest.

2) IPtables is the kernel resident firewall build into ubuntu. by default it allows all conforming traffic, but since ubuntu ships with no open service ports, unless you isntall a service, you don;t need any config. gufw is a common gui tool for configuring it.

3) if you run a linux mailserver for your company, that serves windows hosts, it would be carrear suscide to not scan the mail before delivery.

ubuntu is not immune to attacks but it is much safer than the alternatives. I am a security purest, so I hate it when I see catagorical statements like "you don't need antivirus in linux" but it is true to an extent. if you mean specifically "viruses" (parasitic appllications that spread from host to host, using a specific application to perform actions ) then they are right. if you are refering to "viruses" in terms of all malware (viruses, worms, trojans, rootkits, ad/spyware, botnets etc) then they are wrong.

---

### Post by RedRat on 2009-07-09
If you really are worried I suggest that you install clamav from Synaptic. Load the GUI front end, clamtk. To update the virus signature you will have to run clamtk as root from the terminal using sudo, ie,
sudo clamtk

All we can say right now is that no one has yet written a virus for Linux, but then who knows what tomorrow might bring. Linux, unlike Windows, is based on UNIX and this OS was designed from the beginning to be secure. Windows was designed from the get-go to be a desktop OS isolated from a network. Networking was added piecemeal over the years since windows 3. More and more security has been added to Windows but it is still porous. 

Added to that is the fact that Windows runs on about 90% of the worlds desktop computers. If you want to steal information or money, who you gonna attack. Ya goes where the money is and that is Windows.

---

### Post by Viva on 2009-07-09
> **cazzz said:**
> Viva Are you saying to me Ubuntu Can not infect My vista at all? No way it will Pass Virus To my vista Folders??? I am running Ubutu AS guest and Vista as my main host

No, there are hardly any widespread malware for ubuntu, let alone one that infects a VM host(RedRat covered this host).

---

### Post by cazzz on 2009-07-09
> **viva said:**
> no, there are hardly any widespread malware for ubuntu, let alone one that infects a vm host(redrat covered this host).

thankyou thankyou everyone for detailed explations 10 out of 10

---

