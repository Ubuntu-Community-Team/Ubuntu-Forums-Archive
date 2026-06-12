---
title: "Remote Desktop"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-11-02
I want to remote into my Ubuntu from an outside XP Pro machine.
What do I need to do?

I set up my Remote settings to allow someone in. I set a password.
-  Do I have to be logged off or logged on?
- Do I want to go to whatismyip.com to figure out my public IP?
- Do I need to know my private IP address?
- Do I need to open or port forward any ports on my router?
- Can I also/instead use SSH? (I learned about using that in school, but it's been awhile)

---

### Post by Excedio on 2009-11-02
- Do I have to be logged off or logged on? [COLOR=blue]Logged on.[/COLOR]
[COLOR=#0000ff][/COLOR] 
- Do I want to go to whatismyip.com to figure out my public IP? [COLOR=blue]Yes. I would also suggest setting up a Dynamic DNS name though. [/COLOR][[COLOR=blue]www.no-ip.com[/COLOR]]("http://www.no-ip.com")[COLOR=blue]. Free as in beer.[/COLOR]
[COLOR=#0000ff][/COLOR] 
- Do I need to know my private IP address? [COLOR=blue]Only if trying to use remote access from within your home network.[/COLOR]
[COLOR=#0000ff][/COLOR] 
- Do I need to open or port forward any ports on my router? [COLOR=blue]Yes. Typically ports 5500,5800,5900 TCP/UDP.[/COLOR]
[COLOR=#0000ff][/COLOR] 
- Can I also/instead use SSH? (I learned about using that in school, but it's been awhile)[COLOR=blue] I think this is possible, but I don't know how.[/COLOR]

---

### Post by DapperMe17 on 2009-11-02
Very very easy with NoMachines NXServer, NXNode & NXClient!!

[http://www.nomachine.com/select-package-server.php?id=1&ids=2](http://www.nomachine.com/select-package-server.php?id=1&ids=2)

On your Ubuntu box (the server) Install OpenSSH & SSH from Synaptic. Download the .deb files NXClient, NXNode & NXServer from the above link. Install all three, in exactly that order. (FYI...look for the three orange download links, after you select the Linux .deb link)

If your behind a router, you'll have to "port forward" port 22 to your PC's internal address.

If you have a firewall on Ubuntu, you set a rule to allow port 22.

That's it for Ubuntu.


On your Windows box (the client), just download the free NXClient only, from the same link I provided above. You'll have to set it up via the GUI.


If you want SSH encryption, you'll just have to locate the "public" SSH RSA key from you Ubuntu box, then copy & paste it into the "key" field in your NXClient settings, wich is installed on your Windows box.

If you don't want encryption, you'll "uncheck" the encryption setting in NXClient on your Windows machine.

It's very easy, but might take you a little time if it's your first try. Don't give, up. This is a great "free" suite that absolutely does work. There are good tutorials at NoMachines.

---

### Post by kakashi_12 on 2009-11-03
Ok, I need some serious help here!

First of all, I tried both NX and another app that I found by searching called VNC. Neither of them are working.

- I couldn't download/install them until I finally figured out I had to install an app called Alien. Now I'm able to unzip/archive them. I couldn't get the terminal code to install the aps, and when I did, they were wrong anyways.

- When I did finally unpack the rpm's, I had to put them in my home folder. Then I couldn't figure out which icon would open the actual program. It wasn't stores in the Applications or System menu.

- I'm not sure where all the other apps are actually stored. I should probably unpack this one there as well so it runs right. I'm guessing it was in /etc/ . But I tried unpacking it there, and it wouldn't let me. I must have to be root, which I can't do gui wise.

Now What?!?!!? What's the terminal code to get this stuff installed correctly and to get it working?

---

### Post by kakashi_12 on 2009-11-03
bump

---

### Post by kakashi_12 on 2009-11-03
):P I FINALLY GOT IT!!!!! :) :) :)

I used the vnc app (sorry, it seemed simpler at the time). Then I port forwarded the with the public ip to my internal ip. And it works! woo hoo.

Also, I used Synaptics to install my apps correctly. I'm disregarding the downloaded files via the website. Oh well.

---

### Post by kakashi_12 on 2009-11-03
So now I have another question. I tried logging in via both private and public address. Both worked.
If I were to theoretically have 2 Ubuntu machines up and running and logged on and setup for this...
Then I (from outside the router) remoted in via public IP (of course I can't use private IP outside), how would I specify or pick the particular PC I wish to run?
Would it then prompt me for a login? Would it ask me via computer name? via internal (private) ip address? Would I get some kind of menu choice? Would I get errored out?

---

### Post by nhasian on 2009-11-04
you would use the same public IP address for both computers.  the trick is using a different port number for each computer.  so in your router forward port 5900 to PC#1 and then forward port 5901 to PC#2.  then when you connect, specify which port to connect to.

> **kakashi_12 said:**
> If I were to theoretically have 2 Ubuntu machines up and running and logged on and setup for this...
Then I (from outside the router) remoted in via public IP (of course I can't use private IP outside), how would I specify or pick the particular PC I wish to run?

---

### Post by kakashi_12 on 2009-11-04
Whoa!!! cool! :) thanks.
What if the app (such as vnc, that i use) does not ask for a port. Will it ask for one when I connect do you think? probably not. ok, cool, thanks for the education.
 
Actually, now that I think of it... I think that I read somewhere an example where VNC had the IP and then :0 for a port number after. maybe.

---

### Post by kakashi_12 on 2009-11-04
so now I've got another problem. I forgot, the ports have to be open on both ends. Correct? I'm trying to remote into my ubuntu box from outside at my school domain. I went to viewopenports.com and then typed in vnc's port number it uses and it says closed. So it probably won't work. :(
 
Then I did a search to see what port number Windows XP Remote Desktop uses. Then I typed in that port (to the above website) and it was closed too. I a couple people from here remoted out. But I'm not sure which OS, port, or app they used to do it though. Darn. Any other suggestions on apps to try and ports that I could scan?

---

### Post by badger_fruit on 2009-11-04
I think the websites you went to from your school's network were reporting on the ports open/closed on THAT network, not yours.

The default port for RDP (Remote Desktop Protocol) is 3389 but that can be changed if required.

It is possible for the school to have blocked outbound RDP or VNC connections. If others can connect to their machines at home then you're doing something wrong - probably on your home router/firewall.

Depending on the OS of the target PC (let's assume it's Ubuntu), you need to:-

1. Determine the LOCAL IP address of it.  Run gnome-terminal and type
```
sudo ifconfig
``` This will give you the LOCAL IP address of the "Target PC" (let's call this PC1).

2. Create a new INBOUND RULE on your Firewall or router - instructions vary but the info below will be all you'll need when you find the right section of the configuration tools:-

TCP 5800 (VNC)
TCP 5900 (VNC)

Point ALL of them to PC1's LOCAL IP address.

3. From PC1 visit [www.whatismyipaddress.com](www.whatismyipaddress.com) or [www.ipchicken.com;](www.ipchicken.com;) both will give you your PUBLIC IP address - as someone else mentioned, this may change so consider either asking your ISP for a STATIC IP or learn more about Dynamic DNS services ([www.dyndns.org](www.dyndns.org)).

4. Load up your favourite remote-viewer (eg VNC) on the SOURCE PC (the one at school, let's call this PC2) and point it to the PUBLIC IP address you got in step 3.


That should work.

You may need to do something on the Ubuntu machine to start the VNC service and give it a password, I honestly don't use it as I use SSH to talk with my *nix machines when away from my network at home.  I am sure that someone who can say how to install vnc and configure it will come along and help

I'd guess it would be something like

```
apt-get install vnc
``` and then ```
vncpasswd
``` to set a default password.

Good luck!

---

### Post by kakashi_12 on 2009-11-04
yup i know. that's what i wanted to find out about was if the school's network ports were open that i needed. figured i needed it on both ends.
 
I did get the ip address.
I did port forward port 5900 both udp/tcp on my router to the private IP. Did not try 5800 however.
I did go to whatismyip.com to find my public ip address.
I did install VNC
 
Looks like I got everything you said except the 2nd port. However, I tried it at home (inside the network), and it worked fine. Now that I'm outside, outside the router and modem and internet, don't think it will work.
Unfortunately, I forgot to write down my public IP before leaving the house. But then I ALSO found out the ports were closed on this network. They do have to be open on this side too right? I'm going to try tomorrow with the right IP.

---

### Post by kakashi_12 on 2009-11-04
:popcorn:SUCESS! :)
 
Looks like the port does not have to be open. I finally found the public IP, plugged it in, and it works. Thanks for all your help guys!
 
PS: I love this forum.

---

### Post by DapperMe17 on 2009-11-04
Glad to hear that you figured it out with VNC.


Your problem with NoMachines is that you were downloading the .RPM files :(

Ubuntu uses the .DEB files, which are available at NoMachines.


Alien, is a program that makes .deb files from .rpm files. You don't need that.

:o

---

### Post by kakashi_12 on 2009-11-04
that explains it. thank you for clearing that up! now i got it. deb... of course, ubuntu is a distribution of debian, isn't it?

---

### Post by DapperMe17 on 2009-11-05
Right on!

Don't give up on NX, it's the fastest remote desktop I've used, even while using SSH encryption.

90% of the configurations are automated! 

If you get stuck, we'll help you out. NoMachines website has some good tutorials as well.

---

