---
title: "how to update Wine?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-05-24
Hello,
I have to computers running Ubuntu, a desktop and a laptop. The desktop has updated WINE since yesterday, but the laptop doesnt seem to find any updates for it... could be something wrong with the installation?... I have already working a couple of things on Wine and dint want to uninstall it to seek for the new version 1.2.
For any comments, thanks!

---

### Post by sandyd on 2010-05-24
> **bilbo.san said:**
> Hello,
I have to computers running Ubuntu, a desktop and a laptop. The desktop has updated WINE since yesterday, but the laptop doesnt seem to find any updates for it... could be something wrong with the installation?... I have already working a couple of things on Wine and dint want to uninstall it to seek for the new version 1.2.
For any comments, thanks!
you need to add the WINE ppa for it to update to 1.2
*[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)*

---

### Post by selva.al.raj on 2010-05-24
Hi all,

I'm new here and ubuntu as well.

I have a query related to wine may be i can post it here as i don't want to create a new thread.

I have ubuntu 10.04 LTS. and WINE 1.2-rc1

i have one voip software JUMBLO installed in it. ([www.jumblo.com](www.jumblo.com)).

the application is opening well, but it is not connected to the site. it's not logging in and i'm not able to do calls.

can somebody please help me?

am i doing anything wrong here?

---

### Post by nhasian on 2010-05-24
in case you dont know how to add a ppa, there are detailed instructions from winehq here:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by nhasian on 2010-05-24
I noticed on their website they have a link that says "MAC AND LINUX USERS CLICK HERE" do they have a native linux version?  I tried to access it but it requires signing up with them.

nevermind, it just redirects you to [http://www.linphone.org/index.php/eng](http://www.linphone.org/index.php/eng) 

> **selva.al.raj said:**
> 
i have one voip software JUMBLO installed in it. ([www.jumblo.com](www.jumblo.com)).

the application is opening well, but it is not connected to the site. it's not logging in and i'm not able to do calls.

can somebody please help me?

---

### Post by UpSignal on 2010-05-24
Here you go

> sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine

---

### Post by selva.al.raj on 2010-06-05
> **nhasian said:**
> I noticed on their website they have a link that says "MAC AND LINUX USERS CLICK HERE" do they have a native linux version?  I tried to access it but it requires signing up with them.

nevermind, it just redirects you to [http://www.linphone.org/index.php/eng](http://www.linphone.org/index.php/eng)

thanks hasian. I have installed linphone. but don't understand how use this to call land phone numbers. :( 

i think if somebody can help me to fix the jumblo in wine will be very useful. so far i guess the problem with sharing the internet connectivity with the wine applications.

hope someone can help me.

thanks.

---

### Post by ashwinhgtx on 2010-06-05
> **selva.al.raj said:**
> thanks hasian. I have installed linphone. but don't understand how use this to call land phone numbers. :( 

i think if somebody can help me to fix the jumblo in wine will be very useful. so far i guess the problem with sharing the internet connectivity with the wine applications.

hope someone can help me.

thanks.

Why don't you use something simpler like Skype? You need to pay for the service anyway.

---

### Post by bilbo.san on 2010-06-05
Thanks everyone!
I was added the APP line, however, when running the update, it gives an error with some PUBLIC KEY not authenticated... or something. 

If you guys could help me this one... 
thanks
b.

---

### Post by ashwinhgtx on 2010-06-06
You need to get the proper GPG key from wherever you added the Wine ppa.

---

### Post by selva.al.raj on 2010-06-06
> **ashwinhgtx said:**
> Why don't you use something simpler like Skype? You need to pay for the service anyway.

well.. i was using for long time. i have credit in that. also they are cheaper than skype.

---

### Post by ashwinhgtx on 2010-06-06
> **selva.al.raj said:**
> thanks hasian. I have installed linphone. but don't understand how use this to call land phone numbers. :( 

i think if somebody can help me to fix the jumblo in wine will be very useful. so far i guess the problem with sharing the internet connectivity with the wine applications.

hope someone can help me.

thanks.

Why exactly are you not able to use linphone? It's able to connect to the service provider right?

---

