---
title: "Cannot connect through modem or wifi"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by webcrawler03 on 2009-07-21
Hello! I am very new to the Linux OS in general let alone Unbuntu. I installed it on my laptop (Acer Aspire 5100) several months ago and had problems getting on to the internet so i packed it away and have not touched it since. I believe i found the answer to my wireless problems with MadWiFi for my Atheros wireless card but the problem is i need to be connected to the internet to do it. I have internet on my desktop that im currenly using through my local cable company using a Motorola Surfboard SBV5220 cable modem. I have no problems accessing the internet with it through my Vista based desktop but when i plug the ethernet into my Acer it says something along the lines of aquiring address or something but then it disconnects. So i can not connect to the internet on ubuntu with my cable modem or my wireless card. If anyone can help me connect with my cable modem i can surely get the madwifi app working for my wirless card and that would be great. Better yet if anyone can tell me how to use madwifi without having an active internet connection then my problem would be solved easier. All im hoping for is to acheive some type of internet connection on Unbuntu based Acer. Thank you in advance for any help you provide me.

---

### Post by jbrown96 on 2009-07-21
One problem that I have had with connecting directly to cable modems is that they hard code the mac address. Your modem will only connect to an ethernet card with the mac address (unique address for each network card) of your desktop. Unplug your modem and wait about 30 seconds, then plug it back in. Once it starts up all the way, connect your Acer. You will need to do this again to be able to connect with your desktop.

Edit: The power to your cable modem needs to be disconnected, not the data.

---

### Post by webcrawler03 on 2009-07-21
Great! i am now connected for the first time ever through ubuntu on my laptop! Resetting the cable modem worked great but now on to the wireless card... i downloaded madwifi 0.9.3.2.tar.gz and 
bill@bill-laptop:~$ sudo apt-get -y install build-essential bin86
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
bill@bill-laptop:~$ 

any help on the madwifi would be great

---

### Post by txapelgorri on 2009-07-21
Hi:

Perhaps you are mispelling some word, or maybe your package manager database isn't updated. Could you try this?: open Package Manager, then go to Configuration, then Repositories and then select the repository you want (you can test the most close to your location). Update the Package Manager, and finally find the packages you wish to install.

Cheers, Ibon.

---

### Post by webcrawler03 on 2009-07-21
got the packages to install but im still having some issues and cant get it to work... i will update tonight after work when i have more time to explain but in the mean time if anyone knows any easy ways to get network manager/madwifi to work for me please let me know.

---

### Post by Scunnered on 2009-07-21
**webcrawler03**

I notice that you have not stated which version you are using. I am using 9.04 and my wireless connection worked straight out of the box.  I was able to connect when using the live CD.

If you have not installed Jaunty then that might make things easy for you.

---

### Post by LewRockwell on 2009-07-21
> **Scunnered said:**
> **webcrawler03**

I notice that you have not stated which version you are using. I am using 9.04 and my wireless connection worked straight out of the box.  I was able to connect when using the live CD.

If you have not installed Jaunty then that might make things easy for you.

I was just getting ready to post that...lol.

also, if you are connecting directly from the computer to that modem then you don't have the protection inherent in using a router

where are you getting your wireless signal from?

.

---

### Post by webcrawler03 on 2009-07-22
thank you all so much. I am currently connected through my a wireless network so yes i got it to work. I couldnt understand why i was having so many problems with the madwifi and getting it to work but i found out today about blacklisting ath5 and that seemed to be my solution. i am planning to upgrade to distro 9.04 overnight but in the mean time i do have wireless. no i was not connected through a router, i use my neighbors wireless to connect. and in order for me to get the packages i needed i did have to update my package manager so thank you all so much you each helped a little bit.

---

### Post by Vined Adobo on 2009-07-22
My Acer was not recognized as having a wireless port until 9.04.  I got weary of trying and deleted all of ubuntu.  When I got to mad wifi, I just quit caring.  Now, with 9.04 and very little tweaking, I never boot Windoze.  I love it.  My wife loves it.  My son and DIL love it.  9.04 finally made Linux come of age and can compete with any OS.
Dave

> **webcrawler03 said:**
> thank you all so much. I am currently connected through my a wireless network so yes i got it to work. I couldnt understand why i was having so many problems with the madwifi and getting it to work but i found out today about blacklisting ath5 and that seemed to be my solution. i am planning to upgrade to distro 9.04 overnight but in the mean time i do have wireless. no i was not connected through a router, i use my neighbors wireless to connect. and in order for me to get the packages i needed i did have to update my package manager so thank you all so much you each helped a little bit.

---

