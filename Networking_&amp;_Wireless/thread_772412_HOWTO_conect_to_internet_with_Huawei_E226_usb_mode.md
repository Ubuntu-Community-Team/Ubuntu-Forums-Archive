---
title: "HOWTO conect to internet with Huawei E226 usb modem"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by brentwas on 2008-04-28
hi friends,

recently i connected my usb modem type Huawei E226 on to Ubuntu 8.04
great news is that i was able to access the web after a little google research only.

here are the steps to follow:
1. download from the Add/Remove... tab the 'GNOME PPP' program.
2. it installs in the Applications/Internet pull down menue
3. plug in the E226 modem 
4. modem LED should blink now
5. start the program 'GNOME PPP'
6. enter your username, password and phonenumber. note that most providers have standard phrases or words. if you don't know then check this: [www.taniwha.org.uk/gprs.html](www.taniwha.org.uk/gprs.html)
7. click on 'setup'
8. click on 'detect'
9. change to tab 'networking'
10. depending on your provider adjust IP, DNS settings if needed. also the info is found on [www.taniwha.org.uk/gprs.html](www.taniwha.org.uk/gprs.html)
11. change to 'options' tab
12. activate 'dock in notification area'
13. thats it!
14. click close and now 'connect'
15. it takes abt. 10 secs and you are online.


any question please feel free to ask.
cheers.

---

### Post by servipunto on 2008-09-19
Hi!

having a problem.  We are using this to connect on locations where local internet is hard to find.  The problem we are experiencing is that if the computer for any reason is restarted, we can make the application to open automatically but someone need to come and press the CONNECT button so that it connects to the INTERNET.

Anybody know how we can make it to auto connect or connect to the internet without the need of a person pressing a button?  Thanks very much.

Have a great day!

regards,
EDUARDO

---

### Post by twcook on 2008-09-26
Ubuntu 8.04 - HUAWEI E226 HSDPA USB Modem on an HP Pavillion AMD64.

I recently moved from FC8 to Ubuntu :-)

I used this device under FC8 after much wailing and nashing of teeth.  So I know it works with Linux. 

When I connect using Wvdial directly or GnomePPP I get a valid IP address from the ISP (claro.com.br) but my remote IP is 10.64.64.64 and the 2 DNS servers I get are 10.11.12.13 and 10.11.12.14  

These DNS addresses are what gets registered as the WIN servers when this device is used on a WinXP machine.  On that machine the remote IP is listed as the same as the local IP.  

I seem to recall seeing this on FC8 as well and I have tried many variations in my Init strings but to no avail.  

Anyone have a clue why this happens?

Thanks,
Tim

---

### Post by twcook on 2008-09-28
I (temporarily) solved this issue by starting the internet connection and overwriting my resolv.conf with the DNS servers that really work.  The ideal solution is to get wvdial to honor Auto DNS = no.  I'll submit a bug report there.

---

### Post by luispic on 2008-12-05
twcook, this problem has been discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=963043](http://ubuntuforums.org/showthread.php?t=963043)

hope it helps!

---

### Post by luispic on 2008-12-05
> **servipunto said:**
> Hi!

having a problem.  We are using this to connect on locations where local internet is hard to find.  The problem we are experiencing is that if the computer for any reason is restarted, we can make the application to open automatically but someone need to come and press the CONNECT button so that it connects to the INTERNET.

Anybody know how we can make it to auto connect or connect to the internet without the need of a person pressing a button?  Thanks very much.

Have a great day!

regards,
EDUARDO

EDUARDO, May I suggest using the [wvdial]("http://en.wikipedia.org/wiki/Wvdial") program? it runs on console so you don't have the hassle of dealing with the X server or any "pretty" application, you can run a script very easy at startup.

I'm not sure if you can find it in the repository but give it a try: apt-get install wvdial

---

### Post by jota-e on 2008-12-14
Hi, im new in ubuntu 8.1 and i dont know how to download from add program knome-ppp if i have no internet connection.

i downloaded knome-ppp by windows but i dont know how to install it, some one can tell me in details?
 tks

---

### Post by luispic on 2008-12-14
jota-e, try aptitude (the package handler for ubuntu) just type:

apt-get update 
apt-get install knome-ppp

otherwise, if you use windows to download it, it's most likely that you'll have to compile it in order for it to run in ubuntu, aptitude installs all the applications necessary for it to run well, dependencies and stuff.

the first command will 'update' the database so it has the latest package information.
the secon will install the knome-ppp application it self along with it's dependencies.
you might want to check the file /etc/apt/sources.list (if I'm not mistaking) to see if you have all the "universe" repositories de-commented, if they are commented just remove the # sing in front of them. but for now just try with the commands above, if you have trouble using apt and the whole sources.list post it and I'll help you out.

take care,

---

### Post by axramos on 2008-12-23
Ubuntu 8.10. I use Tigo in Colombia. I was able connect only doing this link says: [http://www.mundolunga.com/2008/11/conxexo-3g-soluo-para-problema-com-dns.html](http://www.mundolunga.com/2008/11/conxexo-3g-soluo-para-problema-com-dns.html)

Uso Tigo en Colombia. Pude conectarme siguiendo las instrucciones del anterior link.

---

### Post by mo0nykit on 2009-10-01
Hello!

What's the point of the first instruction (Add/Remove)? If you can't connect to the Internet in the first place? Can I install Gnome PPP without internet connection? (out-of-the-box Ubuntu)

Thanks!

---

