---
title: "Easy  Remote Control Access Software"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by superprash2003 on 2009-04-01
I often require to remote access other people's computers . But often the client finds it difficult to setup remote control. Crossloop [www.crossloop.com](www.crossloop.com) [http://crossloop.com/ipage.htm?id=predownload](http://crossloop.com/ipage.htm?id=predownload) seems to be the perfect service for me  . The client needs to install that software and provide me with the access code .. Then all i need to do is enter that access code in my machine and then i get instant remote control . This is very simple compared to the port forwarding procedures(port 5900)  etc . 
   Unfortunately crossloop supports only windows and not linux (ubuntu). So im looking for a software/service which provides a similar service for ubuntu. Hope you can help.
 Thanks..
Prash.

---

### Post by primaxx on 2009-04-01
> **superprash2003 said:**
> I often require to remote access other people's computers . But often the client finds it difficult to setup remote control. Crossloop [www.crossloop.com](www.crossloop.com) [http://crossloop.com/ipage.htm?id=predownload](http://crossloop.com/ipage.htm?id=predownload) seems to be the perfect service for me  . The client needs to install that software and provide me with the access code .. Then all i need to do is enter that access code in my machine and then i get instant remote control . This is very simple compared to the port forwarding procedures(port 5900)  etc . 
   Unfortunately crossloop supports only windows and not linux (ubuntu). So im looking for a software/service which provides a similar service for ubuntu. Hope you can help.
 Thanks..
Prash.
Funny you should mention that! For the last couple of days, I've been searching for the same thing. It would make it so much easier to convert friends, collegues etc to Linux if I knew I could just log in to their computers no matter which firewall they were behind.
I have noticed though, that [Logmein]("http://logmein.com") are working on a Linux-solution ([http://www.techworld.com.au/article/280304/logmein_linux_support_coming_year](http://www.techworld.com.au/article/280304/logmein_linux_support_coming_year)). :-)

---

### Post by Excedio on 2009-04-01
[http://www.bomgar.com/](http://www.bomgar.com/)
 
The license is a bit pricey...but worth it if this is trully important to you. Works with Ubuntu users also.

---

### Post by superprash2003 on 2009-04-01
@primaxx thanks.. but doesnt logmein require you to create a user account(verification of email id ) and then click on the ADD button and all that prroecude...
@excedio Thanks , i was looking for a free service though , since i dont use it very regularly..

---

### Post by hyper_ch on 2009-04-02
open-sshserver (and X11 forwarding) is enough for me :)

---

### Post by aeiah on 2009-04-02
ultravnc offers a small downloadable java app that may be useful. we use it occasionally for desktop support. you get the user to click a link on a page you're hosting, and it downloads the small java client and starts it running. they then connect to your listen server.

now, the java client works in linux, but i dont think the listen server does. however, its vnc. perhaps other vnc software does work.

---

### Post by scorp123 on 2009-04-02
> **hyper_ch said:**
> open-sshserver (and X11 forwarding) is enough for me :) Also: reverse SSH + a VNC instance. More than enough. I did that for my (elderly) father. He has an icon on his desktop: "Get help". He clicks that and what happens behind the scene is that his machine establishes a reverse SSH connection to me. All I need to do is to "ride back" on that connection and Bingo!: I'm on his desktop.

---

### Post by dmizer on 2009-04-02
> **scorp123 said:**
> Also: reverse SSH + a VNC instance. More than enough. I did that for my (elderly) father. He has an icon on his desktop: "Get help". He clicks that and what happens behind the scene is that his machine establishes a reverse SSH connection to me. All I need to do is to "ride back" on that connection and Bingo!: I'm on his desktop.

I do the same thing, except I don't ever use VNC as I've not found a need for it.

I send people "magic words":

```
ssh -R 10002:localhost:22 me@my-machine
```

Than I tell them to hit alt+f2, paste the magic words in the box, put a checkmark in "run in terminal", and click "run".

Then I can connect to their machine with this
```
ssh -C them@localhost -p 10002
```
(-C switch is just for compression)

Works every time.

---

### Post by scorp123 on 2009-04-02
> **superprash2003 said:**
> I often require to remote access other people's computers . But often the client finds it difficult to setup remote control.  Example for Linux:

[LIST]
[*]the one wanting your help has to enable "Remote Desktop" in Ubuntu
[*]the one wanting your help then has to execute this command (best thing would be to put that as a launcher icon onto the desktop!):
[/LIST]
```
ssh -R 8210:localhost:22 -p 2210 valid-user@your.ip.here

```
This will give you a SSH server on your own installation waiting for connections on port 8210. Now, to connect to this, you'd do:
```
ssh -p 8210 valid-remote-user@localhost
``` ... and you'd be logged into the machine where the connection originated.

Now, as the "Remote Desktop" feature is running, you could use a "vncviewer localhost:0" and you'd get to see the remote desktop.

Above example is not really elegant, to make it more elegant you'd probably need to add more ports.

Windows users can do something similar with "Putty". There are dialogues in the "Putty" client (SSH option configuration) which allow you enter the same options into the right fields. If a Windows user forwards e.g. port 3389 (= RDP!) to your machine you'd be able to see their exported desktop via a RDP client (e.g. "tsclient", "rdesktop", etc.).

The beauty here is that you don't need any additional software, it's basically all already there in the Ubuntu OS. :)

---

### Post by scorp123 on 2009-04-02
ah, dmizer was faster :D

---

### Post by dmizer on 2009-04-02
> **scorp123 said:**
> ah, dmizer was faster :D

sorry ;)

---

### Post by superprash2003 on 2009-04-02
Thankyou so much for the replies . But again , the procedures mentioned are a bit complex for the clients to follow . Also i need this one solution to work with windows and linux clients . 
  For clients to enter details in putty and configuring the ports etc.. It could be really difficult . I was hoping for something like crossloop where you just run the app and pass on the access code to access the pc.

---

### Post by scorp123 on 2009-04-02
> **superprash2003 said:**
> For clients to enter details in putty and configuring the ports etc.. It could be really difficult You could do that, e.g. in a Windows virtual machine. And then you just send them your pre-configured "putty.cfg" file. That should be easy enough I suppose?

In the case of Windows you just have to make sure that the RDP port 3389 gets forwarded back to the originating host. That's it. It's very easy.

Google just spitted out this:
[http://www.downloadsquad.com/2007/02/01/howto-transfer-your-putty-settings-between-computers/](http://www.downloadsquad.com/2007/02/01/howto-transfer-your-putty-settings-between-computers/)

I guess that would help?

---

### Post by dmizer on 2009-04-02
> **superprash2003 said:**
> Thankyou so much for the replies . But again , the procedures mentioned are a bit complex for the clients to follow . Also i need this one solution to work with windows and linux clients . 
  For clients to enter details in putty and configuring the ports etc.. It could be really difficult . I was hoping for something like crossloop where you just run the app and pass on the access code to access the pc.

Simply because of the difference between the two systems, I don't think you're going to find one way to access both Windows and Linux clients. I vaguely recall seeing some kind of web based app for this, but I can't find it and I think it required a local server. However, my feeling is that, just as with other software, you'll have to use one way for Linux, and another for Windows. The two systems are just too different.

The method I outlined has worked on even the most technically challenged of my Linux users. It's 4 extremely simple steps, of which the most complicated is copy/paste. You'll have to do some configuration ahead of time (public keys), but otherwise it's cake for the user. You can use the method to do simple CLI edits, or for X forwarding, or even for VNC tunneling.

Honestly, I don't use any kind of remote access on any of my Windows clients. I feel it's too dangerous. The only thing I can think of for Linux -> Windows is a cross platform java type desktop sharing app, and that's unlikely to be easy for technically challenged users. After a quick search, I only found two with promise, and I haven't tried either of them:
[https://jxta-remote-desktop.dev.java.net/](https://jxta-remote-desktop.dev.java.net/) (early development)
[http://sourceforge.net/projects/jrdesktop/](http://sourceforge.net/projects/jrdesktop/) (under development)

That said, I never thought of trying a putty.cfg file like scorp123 suggested, and that should be dead simple too. Just have the user double click on it and off you go. I'll have to test that with my elderly and click challenged father. If he can do it, anyone can ;)

---

### Post by HermanAB on 2009-04-02
This one is the easiest of them all:
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)

---

### Post by superprash2003 on 2009-04-03
thank you so much for your replies. Since most of my clients use windows , the last solution given by herman seems to be pretty easy.. Thanks herman for that..
  For linux i would use the "magic words" :) ( thanks dmizer) .. Thanks scorp123 and everyone else who replied..

---

### Post by KayakJim on 2009-04-03
You might want to check out [LogMeIn]("https://secure.logmein.com/home.asp?lang=en") Free.

---

### Post by CyberMando on 2009-04-03
gitso
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)
does this. it is a little new but works for me. I would have to say the ssh solutions are much better though. :)

---

### Post by scorp123 on 2009-04-04
> **CyberMando said:**
> gitso
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)
does this. it is a little new but works for me.

I got curious and just tried it. It's indeed very very easy and it works across platforms. A friend on Windows was able to send me his desktop, and I'm using Ubuntu. The other way around worked too. Port 5500 TCP needs to be open on the side of the one giving help (you have to make sure that NAT + port forwarding is correct and that firewalls let the traffic through, etc.). The one requesting your help just needs to know your external IP address or your (Dyn-)DNS name, and that's it. The rest is handled by Gitso.

I'd still prefer my reverse SSH tunnels because they offer a lot more flexibility (you can freely choose what ports you want to forward) but Gitso is clearly very useful in cases where people don't have SSH clients on their OS (e.g. Windows?) and getting them to install + configure "Putty" correctly would take too much time.

---

### Post by noelvh on 2009-04-04
I help a number of people remotely and they use windows. I have played around with VCN for a number of years and found this. showmypc.com. Fro the host they go to the web site download the smal file and run it. On you end you launch the java app and waite for the code from the host. The only draw back it the conntection is only good for an hour. But I find with the fact you have to reboot windows 5 time to fix any real issues this dose not hinder me and the end user. 

the best part you do not have to bother with fire wall, and ports it just works.

Noel
[http://showmypc.com/](http://showmypc.com/)

---

### Post by superprash2003 on 2009-04-05
gitso surely looks simple . i guess this was exactly what i wanted.. thanks cybermando

---

### Post by devilgas on 2009-09-28
> **hyper_ch said:**
> open-sshserver (and X11 forwarding) is enough for me :)
 Can you help me setup my box so I can get to it over the LAN from my Windows PC?

---

### Post by devilgas on 2009-09-28
> **dmizer said:**
> I do the same thing, except I don't ever use VNC as I've not found a need for it.
 
I send people "magic words":
 
```
ssh -R 10002:localhost:22 me@my-machine
```
 
Than I tell them to hit alt+f2, paste the magic words in the box, put a checkmark in "run in terminal", and click "run".
 
Then I can connect to their machine with this
```
ssh -C them@localhost -p 10002
```
(-C switch is just for compression)
 
Works every time.
Can I get that to work on my lan?  I want to connect to the ubuntu box from my windows pc and have access to its desktop?

---

### Post by dmizer on 2009-09-29
> **devilgas said:**
> Can I get that to work on my lan?  I want to connect to the ubuntu box from my windows pc and have access to its desktop?

You don't need that trick to make it work on a LAN. The quoted trick is a work around to bypass a remote firewalled system. Just use [Putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/") in Windows and make sure to enable X11 forwarding.

---

### Post by little_penguin on 2009-10-04
As an alternative, if you want a web-based solution which is easier to set up by the person you are connecting to, you could also use either NTRConnect:

[http://www.ntrconnect.com]("http://www.ntrconnect.com/")

or

or Teamviewer in Wine. 

[http://www.teamviewer.com]("http://www.teamviewer.com/")

---

