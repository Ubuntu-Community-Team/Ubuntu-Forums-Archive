---
title: "Remote Desktop"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Jason Cook on 2009-10-02
I would like to know of a program I can use to connect to my Windows XP from another computer. I would like to have one that can be used from a web browser so I can use it on multiple computers without installing software on them.

---

### Post by Paddy Landau on 2009-10-02
[LogMeIn]("http://logmein.com/") -- The server can be Windows or Mac. The client can be Windows, Mac or Linux, all from a browser.

---

### Post by blueridgedog on 2009-10-02
VNC has a web interface.

---

### Post by little_penguin on 2009-10-04
NTRConnect is web-based with good encryption and is available for Linux, Windows and Mac.
The free version only allows you to connect to up to 2 computers, though. Otherwise it's pretty good and means there's no need to do any port forwarding on routers etc.

[www.ntrconnect.com]("http://www.ntrconnect.com")

---

### Post by grturner on 2009-10-04
vnc has a java viewer... that would be my vote.

---

### Post by antony.s on 2009-10-04
I just saw [http://www.nomachine.com/](http://www.nomachine.com/) posted in another thread, but never tried it so no idea if it's good :)

---

### Post by Jason Cook on 2009-10-08
> **Paddy Landau said:**
> [LogMeIn]("http://logmein.com/") -- The server can be Windows or Mac. The client can be Windows, Mac or Linux, all from a browser.
  I am using LogMeIn right now. I haven't tried any of the others yet. I would it would be nice to have sound on the remote machine (which you can only get with the pro version).
      
      > **blueridgedog said:**
> VNC has a web interface.
      I haven't been able to get VNC working. I tried doing that before I posted but I couldn't get it to work. I tried to configure the router to allow connection but only works on the local network.
      
      > **little_penguin said:**
> NTRConnect is web-based with good encryption and is available for Linux, Windows and Mac. The free version only allows you to connect to up to 2 computers, though. Otherwise it's pretty good and means there's no need to do any port forwarding on routers etc. [www.ntrconnect.com]("http://www.ntrconnect.com/")
     I haven't tried this yet I will try this when I get a chance.
      
      > **antony.s said:**
> I just saw [http://www.nomachine.com/](http://www.nomachine.com/) posted in another thread, but never tried it so no idea if it's good :)
   This is not what I am looking for. I want to be able to connect from a web browser as I need to connect from places where I can't install applications

---

### Post by lavinog on 2009-10-08
> **Jason Cook said:**
> This is not what I am looking for. I want to be able to connect from a web browser as I need to connect from places where I can't install applications

What about portable apps that can be ran from a flash drive?

Without java installed, you might not be able to remotely access using a browser.

---

### Post by Jason Cook on 2009-10-08
> **lavinog said:**
> What about portable apps that can be ran from a flash drive? Without java installed, you might not be able to remotely access using a browser.

I do use Portable Apps and Portable Java but most computers I use have Java installed. What I am meaning is that program he is suggested requires another program (non-portable) to be installed. I want to be able to connect without installing that software.

---

### Post by Paddy Landau on 2009-10-08
> **Jason Cook said:**
> I am using LogMeIn right now. I haven't tried any of the others yet. I would it would be nice to have sound on the remote machine (which you can only get with the pro version).
I'm happy with LogMeIn. It's worked for me from its first installation, and given no problems whatsoever. I access Windows machines from my Linux machine. It's obviously a well-tested app.

Having sound as well would be nice, but fortunately sound isn't a must-have.
      
      > **Jason Cook said:**
> I haven't tried this yet [[www.ntrconnect.com]("http://www.ntrconnect.com/")] I will try this when I get a chance.
Please let us know how you find it, if you try it.

---

### Post by halitech on 2009-10-08
> **Paddy Landau said:**
> I'm happy with LogMeIn. It's worked for me from its first installation, and given no problems whatsoever. I access Windows machines from my Linux machine. It's obviously a well-tested app.

Having sound as well would be nice, but fortunately sound isn't a must-have.
      
      
Please let us know how you find it, if you try it.

Have you noticed any issues with LogMeIn lately? I've got 2 systems that must have updated software that refuse to work anymore. I can log in but the remote control window is black and seems to be wanting to use ActiveX now instead of Java. Also can't find any place to select Java anymore either. 2 other systems still work fine (not sure on the versions). This could potentially be a killer for me as I don't want to have to use Windows in a VM to remote control systems (nor do I want to go back to 32bit to use the LogMeIn applet)

---

### Post by Paddy Landau on 2009-10-08
> **halitech said:**
> Have you noticed any issues with LogMeIn lately?
No, I haven't.

The remote computer is set up to automatically update when updates are available, and apparently there was one recently. It continued to work well for me. The initial web interface has changed in appearance, but other than that, everything has continued to work. I last accessed it yesterday.

I was unaware that there was a choice between ActiveX and Java; I just use what the browser gives me.

I've just checked, and now I realise that LogMeIn uses a plugin for Firefox.

---

### Post by halitech on 2009-10-08
> **Paddy Landau said:**
> No, I haven't.

The remote computer is set up to automatically update when updates are available, and apparently there was one recently. It continued to work well for me. The initial web interface has changed in appearance, but other than that, everything has continued to work. I last accessed it yesterday.

I was unaware that there was a choice between ActiveX and Java; I just use what the browser gives me.

I've just checked, and now I realise that LogMeIn uses a plugin for Firefox.

thats what I was wondering about, the 2 it doesnt work on just had the software reinstalled and and giving me the black screen. I think it had ActiveX, Java and html(very slow and actually refrseshes the screen on click)

Are you using the 32bit version? When I checked yesterday it only had the 32bit firefox plugin (I'm using 64bit)

---

### Post by Paddy Landau on 2009-10-09
> **halitech said:**
> Are you using the 32bit version?
Yes, 32-bit.

---

### Post by halitech on 2009-10-09
> **Paddy Landau said:**
> Yes, 32-bit.

ok, its probably the plugin you have that is allowing LogMeIn to work with the new update that I can't run due to using 64bit. Guess I'll have to keep the VM around with windows XP for when I need to use it.

---

### Post by Paddy Landau on 2009-10-09
> **halitech said:**
> ok, its probably the plugin you have that is allowing LogMeIn to work with the new update that I can't run due to using 64bit. Guess I'll have to keep the VM around with windows XP for when I need to use it.
LogMeIn has a knowledge base, a forum, and a method to submit support tickets.
[https://secure.logmein.com/UK/support/free/](https://secure.logmein.com/UK/support/free/)

---

### Post by halitech on 2009-10-09
been looking around and seems alot of people are having issues with version 4 of LogMeIn but I just checked the 2 systems that are working and they have version 4 so not sure whats going on unless it is because they were set to Java before the upgrade. I don't know but will follow up with LMI.

---

### Post by Paddy Landau on 2009-10-11
I've just had a closer look at [ntrconnect.com]("https://www.ntrconnect.com/").

Despite its website claiming that it works with Windows, Mac and Linux, it seems that the server must be only Windows or Mac (as with [LogMeIn]("https://secure.logmein.com/")).

If you have problems with LogMeIn, you might want to try it.

---

### Post by Paddy Landau on 2009-10-11
And now I've tested [Yuuguu]("http://www.yuuguu.com/").

It's quite a lot slower than LogMeIn, and I struggled somewhat to find the relevant buttons...

BUT...

It works on Linux! (Without having to mess around with routers.)

The server must have Yuuguu installed. The client may have it installed, or may access via a browser.

Yuuguu doesn't have the same features as LogMeIn, but for personal use it's fine.

The one restriction compared to LogMeIn that I found was that the server (remote) computer cannot be accessed unattended, which is sometimes a requirement for me.

---

### Post by Jason Cook on 2009-10-11
I am installing this right now. Thanks!

---

### Post by CharlesA on 2009-10-11
To connect to my windows machines I SSH to my server and then use vncviewer from there. Works like a charm for me, and I only need to have 1 port open to the internet.

I don't know if that would work with vnc java or not tho.

---

### Post by little_penguin on 2009-10-11
@Paddy Landau

NTRConnect actually works with Linux as the server as well, I've been connecting to another Ubuntu computer (server) from Ubuntu / Windows without any problems, and the speed is pretty decent.

When I installed it a month ago, clicking the Download button detected I had linux automatically and presented the relevant version, but I've just checked what happens now and it seems you just get presented with a zipped Windows installer. So could be they've removed the linux download since? Maybe they handed the project over to Freshmeat?

You can also get the NTRConnect linux installer here:

[http://freshmeat.net/projects/ntrconnectremoteaccessforlinux/](http://freshmeat.net/projects/ntrconnectremoteaccessforlinux/)

---

### Post by Paddy Landau on 2009-10-11
> **little_penguin said:**
> NTRConnect actually works with Linux as the server... could be they've removed the linux download since?
Thanks for letting me know. That makes it sound as though the company no longer supports the Linux version. I would not want to go with NTRConnect if that is the case.

It may be worth asking the Support team.

---

### Post by Jason Cook on 2009-10-11
> **Paddy Landau said:**
> Thanks for letting me know. That makes it sound as though the company no longer supports the Linux version. I would not want to go with NTRConnect if that is the case. It may be worth asking the Support team.
I don't think that it supports Linux anymore. When I tried to connect to my computer via NTRconnect I get the message :(.
[quote=NTRconnect]```
REMOTE CONTROL OPTION NOT AVAILABLE UNDER LINUX OS
```[/quote]

---

### Post by Jason Cook on 2009-10-12
Does anyone know of a VPN server that can be installed on Ubuntu (or even better, a portable, cross-platform one)? If so then I think that I have found a way to use your hardrive and printer with LogMeIn Free. You could create a VPN connection on your computer, share your files and printers over the network, and connect to the VPN from your Windows computer. Please tell me if this is even possible or if it can't be done.

---

### Post by Paddy Landau on 2009-10-12
> **Jason Cook said:**
> Does anyone know of a VPN server that can be installed on Ubuntu (or even better, a portable, cross-platform one)? If so then I think that I have found a way to use your hardrive and printer with LogMeIn Free. You could create a VPN connection on your computer, share your files and printers over the network, and connect to the VPN from your Windows computer. Please tell me if this is even possible or if it can't be done.
As I understand, you can just install a normal VPN in order to do that. I've used VPN only to share a folder, so I'm no expert, but have a look at the [Open VPN instructions]("http://openvpn.net/index.php/open-source/documentation/howto.html"). It's somewhat fiddly to set up, and again needs fiddling with the router (boo!), but once set up it works.

I wish that things like VPN, VNC and so on had peer-to-peer connection, just as Skype, LogMeIn and so on do,  instead of having to forward ports via routers. It makes them so unportable!

---

### Post by Jason Cook on 2009-10-13
> **Paddy Landau said:**
> It's somewhat fiddly to set up, and again needs fiddling with the router (boo!), but once set up it works. I wish that things like VPN, VNC and so on had peer-to-peer connection, just as Skype, LogMeIn and so on do,  instead of having to forward ports via routers. It makes them so unportable!
I would need something that has peer-to-peer connection as this is a laptop. There is no point in setting up my router for VPN when can just walk to the computer;)

---

### Post by Jason Cook on 2009-10-15
bump

---

### Post by Paddy Landau on 2009-10-16
> **Jason Cook said:**
> bump
Jason, if I've understood you correctly, this is a new question. I would suggest that you start a brand new thread for it.

---

