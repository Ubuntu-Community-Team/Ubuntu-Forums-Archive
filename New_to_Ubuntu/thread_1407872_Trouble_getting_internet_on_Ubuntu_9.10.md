---
title: "Trouble getting internet on Ubuntu 9.10"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by HPwriterKyle on 2010-02-15
Hey guys,

I'm a relatively new Ubuntu user, and although I know my way around the OS pretty well, I just can't seem to get the internet connected.  I live in a dorm at the University of Louisville, and I've been trying to connect through the ethernet cable that I have here.  

I dualboot Ubuntu 9.10 with Vista, and they both work flawlessly together.  My university uses Cisco CleanAccess Agent to control who has access to the Uni's internet.  Usually all I have to do is enter my login info into the Agent, and I have access all day.  I've tried using ipconfig to get the info needed for connection manager, but I still can't connect when I'm on Ubuntu.  Both OS's are the 64-bit versions.

Can someone help me with this problem?  Or is there another distro I should get that automatically detects an internet connection?  Any help is appreciated!

HPwriterKyle

---

### Post by mechro on 2010-02-15
Reading various Uni FAQs on the internet says try...

Open a browser, try browsing e.g. [http://www.google.com](http://www.google.com) then hopefully some sort of authenticating web page should appear where you enter your login info.

---

### Post by tom.swartz07 on 2010-02-15
> **mechro said:**
> Reading various Uni FAQs on the internet says try...

Open a browser, try browsing e.g. [http://www.google.com](http://www.google.com) then hopefully some sort of authenticating web page should appear where you enter your login info.

I have the same problem on my campus at the University of Scranton. ResNet sucks when it comes to things like this....

Im not sure if you have Internet2 on your campus, but for some reason Clean Access, Internet2, and Ubuntu do not mix. Luckily, Internet2 on university campuses is usually implemented through the wired ethernet connections.

Heres what Ive found when it comes to internet and Clean Access. 

1.) When you first turn on your computer after its been shut down, you will need to assure that its only running on wireless. Connect to your network, then open a browser. Clean Access will redirect your homepage to their login; type your credentials and youre all set (I somehow managed to get Google Chrome to save the login, so all I need to do is click the button and im in)

2.) Try to avoid the wired connections. It sounds counter-intuitive, but believe me- if you try to talk to your network admin to have them manually bypass you on CCA, you're in for about 3 hours of questioning and security fights. Being 'whitelisted' on CCA is the only way for you to access wired internet while on Ubuntu, just because of the way that the program is designed (it doesnt handle unix systems well, it basically is there to cover Windows only)

3.) If you ever do have a problem with your internet, try to seek out other Linux users on campus first, before going to the ResNet desk. I had 3 full time workers at the help desk tell me that my version of Ubuntu was 'illegal and infringed on copy protection'. OBVIOUSLY they have no idea what the heck Linux is based upon. When you seek the help of other Linux users on campus, Im sure that they have been through the same routine and runaround, and they could provide in-depth help on how to 'get around' CCA's limits.


Also, you may notice that if you log in to CCA under Windows (wifi only), restart into Ubuntu, you will still be connected. Thats because CCA filters based on Wireless card MAC address only, once its registered to an IP, youre set. Granted, if you login under windows, shut down, then 30 min later boot to Ubuntu, you wont be logged in, but its a great convenience when youre doing a quick switch to your other OS

Hope this helps!

---

### Post by HPwriterKyle on 2010-02-15
Thanks for responding!

I really don't use my Uni's wifi that often, only when i am in one of my classes, and during that time I have to use windows anyway because it's a C# class.

I really need to figure out a way to make ubuntu work with ethernet.  When I bring up a web browser, it doesn't redirect me because it's not wireless.  It just shows a no connection page.  

I just need to figure out what to put into the connection manager, or into terminal, to make it work.  After all, CCA isn't exactly running while i am not in windows. 

Does anyone know how to do this?  I'll give you any info that you need.

---

### Post by tom.swartz07 on 2010-02-15
> **HPwriterKyle said:**
> Thanks for responding!

I really don't use my Uni's wifi that often, only when i am in one of my classes, and during that time I have to use windows anyway because it's a C# class.

I really need to figure out a way to make ubuntu work with ethernet.  When I bring up a web browser, it doesn't redirect me because it's not wireless.  It just shows a no connection page.  

I just need to figure out what to put into the connection manager, or into terminal, to make it work.  After all, CCA isn't exactly running while i am not in windows. 

Does anyone know how to do this?  I'll give you any info that you need.

Sure!

You could *try* disabling IPV6, perhaps that is what is causing the malfunction. [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

I should reiterate here; because Cisco Clean Access Agent is designed to limit access for Windows machines that may be infected with viruses, CCA doesnt work for Ubuntu- you knew that already. 
What you may not have known is that CCA has a web-based login that you could use. Mac users use this to get on to the network, as do Linux users. Unfortunately, I have only ever been able to make this work over WiFi- (the help desk wasnt too helpful either). Its a minor inconvenience to only run on wifi, rather than bridged wifi + ethernet, but there isnt that much of a marked difference. On my network, I have up/down speeds of 287kbps :-\":biggrin:


Let me know if you have any luck with ethernet after disabling IPV6; other than that, there isnt much you could do for wired connections.


Also, do you know that C# is supported in Ubuntu? [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)
You have built in compilers for C, C+, C++ and C#, along with Python, (and with the installation of ubuntu-restricted-extras package) Java and Javascript.

Open gEdit and scroll through the list to see what all you can write in code

---

### Post by HPwriterKyle on 2010-02-15
Yeah, it's just easier to work with C# in Windows, since it was meant for that OS anyway.  In my class, we have to use Visual Studio, we aren't allowed to use any other compiler.

How exactly do I disable IPv6, and what do I do after that?

I feel really nooby here :\

---

### Post by tom.swartz07 on 2010-02-15
> **HPwriterKyle said:**
> Yeah, it's just easier to work with C# in Windows, since it was meant for that OS anyway.  In my class, we have to use Visual Studio, we aren't allowed to use any other compiler.

How exactly do I disable IPv6, and what do I do after that?

I feel really nooby here :\

No big, I guess its a matter of preference.

This will only work if your using Grub2; If youre on Karmic, youre using Grub2.
```
gksudo gedit /etc/default/grub
```
Look for this line and add:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```
Save and close your file then run:
```
sudo update-grub2
```
Reboot and give it a try.

---

### Post by HPwriterKyle on 2010-02-15
How do you save something when it's in Terminal?

Or am I a complete noob and we're not talking about Terminal here?

---

### Post by tom.swartz07 on 2010-02-15
> **HPwriterKyle said:**
> How do you save something when it's in Terminal?

Or am I a complete noob and we're not talking about Terminal here?

Im not sure what youre asking.

When you enter the gksudo gedit command, it will open a text editor, just simply save it <CTRL+S> and then close the window.

then just run the update grub command and restart the computer.

---

### Post by Miljet on 2010-02-15
When you type ```
gksudo gedit /etc/default/grub
``` in the terminal, it will open gedit, which is a text editor. Once you save your work and close gedit, you will be returned to the terminal.

---

### Post by HPwriterKyle on 2010-02-15
Oh, okay, I get it.

I'll try this in an hour or so (watching a show atm) and let you know how it went.

Thanks for your help, whether it works or not. :)

---

### Post by HPwriterKyle on 2010-02-15
Well, I did all you said, but sadly my internet still wouldn't work.  :(

I think I am going to try using my MAC address.  Do you think this will work?

---

### Post by HPwriterKyle on 2010-02-15
Okay, so I couldn't get my MAC address because Ubuntu does not even realize that I am connected via an ethernet cable.

So my question is, how do I make Ubuntu know that I have a freaking cable going into my laptop?

---

