---
title: "file transfer from laptop to desktop"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by numbness05 on 2009-08-10
Hey there..

I have my desktop and my laptop both running ubuntu 8.10.

But I have a whole load of data on the laptop that needs transfering over to the desktop about 80gb of it actually.

I have been given a straight through cable and was told to use that to connect the two machines to undergo this task but when I connect them nothing happens..

Am I missing something here? I was told just to connect to plug in and they would see each other...

Is there software that I need or a program I need to run to make the two machines see each other?

Many thanks

---

### Post by arochester on 2009-08-10
I think it's a crossover cable you need...

---

### Post by numbness05 on 2009-08-10
i'm sure thats what I have been given
the guy that gave it to me has a fair knowledge of computers and knew whjat i wanted to do maybe i just have the name wrong...

so assuming it is a cross over cable what would I do to achieve what it is i have set out to do please?

Thanks again.

---

### Post by asmoore82 on 2009-08-10
Let's say you have two machines named *apple* and *orange*.

On apple, install the Filezilla Client:
```
sudo apt-get install filezilla
```
On orange, install the OpenSSH Server:
```
sudo apt-get install openssh-server
```

Then connect them with the crossover ethernet cable - it should look like an overgrown phone cord.
On apple, open Filezilla and fill in the 4 boxes at the top:
Host: orange.local
Username: your username *_on orange_*
Password: your password *_on orange_*
Port: 22
and click QuickConnect.

Now you should have a file browser for apple on the left, and orange on the right;
and you can simply drag and drop files and folders between the two.

While this could be done a little easier with nautilus instead of filezilla,
nautilus seems to have some weird performance bugs right now,
so filezilla will probably be much better in the long run.

---

### Post by numbness05 on 2009-08-10
> **asmoore82 said:**
> Let's say you have two machines named *apple* and *orange*.

On apple, install the Filezilla Client:
```
sudo apt-get install filezilla
```
On orange, install the OpenSSH Server:
```
sudo apt-get install openssh-server
```

Then connect them with the crossover ethernet cable - it should look like an overgrown phone cord.
On apple, open Filezilla and fill in the 4 boxes at the top:
Host: orange.local
Username: your username *_on orange_*
Password: your password *_on orange_*
Port: 22
and click QuickConnect.

Now you should have a file browser for apple on the left, and orange on the right;
and you can simply drag and drop files and folders between the two.

While this could be done a little easier with nautilus instead of filezilla,
nautilus seems to have some weird performance bugs right now,
so filezilla will probably be much better in the long run.

ok all this seems to works lovely up until the point where I ask it to quick connect and it "orange" doesn't find "apple"
I have altered the IPv4 setting to link-local only is this right?
only all I'm getting is 
Error:	ssh_init: Network is unreachable
Error:	Could not connect to server.

thank you

---

### Post by cariboo on 2009-08-10
What are the ip addresses of the two computers, as they have to be in the same netblock?

[list]
[*]apple  192.168.0.1
[*]orange 192.168.0.2

You can set the ip addresses using network manager.

---

### Post by Cotopaxi on 2009-08-10
Very crazy comment:

1)
plug in an external USB hard drive into the laptop.

2)
On your file browser pull down the &#8220;view&#8221; menu and select &#8220;show hidden files&#8221;

3)
Now select your &#8220;home&#8221; folder

4)
pull down the &#8220;edit&#8221; menu and select &#8220;select all&#8221;

5)
Copy all that to your external hard drive

6)
Go for a lovely weekend trip (just joking)

7)
Now do the reverse operation, pluging the external drive into your desktop.

It looks really stupid, but you are actually only working a few minutes, the rest of the time one of the two computers is working.

I have done it a couple of times and it is just the easiest way to go!

---

### Post by mapes12 on 2009-08-10
Hello numbness05

In my experience you need nothing more than ssh.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through.

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig
```

this should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
your output can differ quite a bit, but the imporant information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

That's it!

Hope this helps.

EDIT: The cable should not matter. The ssh server will work it out itself.

Mark

---

### Post by numbness05 on 2009-08-10
> **Cotopaxi said:**
> Very crazy comment:

1)
plug in an external USB hard drive into the laptop.

2)
On your file browser pull down the “view” menu and select “show hidden files”

3)
Now select your “home” folder

4)
pull down the “edit” menu and select “select all”

5)
Copy all that to your external hard drive


6)
Go for a lovely weekend trip (just joking)

7)
Now do the reverse operation, pluging the external drive into your desktop.

It looks really stupid, but you are actually only working a few minutes, the rest of the time one of the two computers is working.

I have done it a couple of times and it is just the easiest way to go!



Trust me if I had an external Hard drive that worked I would.
unfortunately my one has just died with all my data on hence wanting to transfer it from laptop... he he he:P

---

### Post by numbness05 on 2009-08-10
> **mapes12 said:**
> Hello numbness05

In my experience you need nothing more than ssh.

1.) Make sure the openssh-server is installed on both machines. You can check in Places>Connect to Server and make sure SSH is an option in the service type drop down box. If it isn't installed then type this command in both computers Terminal and let them run through.

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer this is important to address the computers. use the following command to obtain your computers IP-Address

```
ifconfig
```

this should give you an output just like this one


your output can differ quite a bit, but the imporant information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.1.68

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server.
- Choose SSH as the at the service type
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This would be the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click ok
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

Bandwidth and external security should not be an issue because you are deploying your local network and not going out over the internet. Also, ssh is Secure Shell which is designed to be just that i.e. secure.

That's it!

Hope this helps.

EDIT: The cable should not matter. The ssh server will work it out itself.

Mark


ok this seems to make more sense...

but excuse my ignorance.. How should the two machines be connected?
Do i use the crossover lead an Ethernet lead or the wireless network?

Thanks once again for your patience.

---

### Post by numbness05 on 2009-08-10
[QUOTE=cariboo907;7763949]What are the ip addresses of the two computers, as they have to be in the same netblock?

[list]
[*]apple  192.168.0.1
[*]orange 192.168.0.2

You can set the ip addresses using network manager.[/QUOTE

Sorry the ip addresses are the same...?

---

### Post by numbness05 on 2009-08-10
Ok so SSH seems to work but only one way lol and typically not the way I need it only sees my desktop from my laptop cant get it to work in reverse...

although I'm wondering the ip addresses look completely different  example the desktop starts 169.254.8.145 and the laptop 169.254.8.9....the 9 on the end looks kinda lonely by comparison to the desktop one which has 3 digits is this right? I just keep getting connection refused by server...

---

### Post by asmoore82 on 2009-08-10
those strange 169 addresses are the results we want... they are "fake" addresses
where the system has realized that it is not connected to the Internet
but has auto-config'ed a semi-random address for local communication...

If you have filezilla connected and working, you can send or receive in both directions.

If you must run filezilla from a specific computer for whatever reason,
switch your apples and oranges and rinse and repeat.

---

### Post by numbness05 on 2009-08-10
> **asmoore82 said:**
> those strang 169 addresses are what we are after... they are "fake" addresses
where the system has realized that it is not connected to the Internet
but has auto-config'ed a semi-random address for local communication...

If you have filezilla connected and working, you can send or receive in both directions.
 
I have filezilla installed but for some reason that doesn't seem to connect to my laptop either...

---

### Post by mapes12 on 2009-08-10
> ok this seems to make more sense...

but excuse my ignorance.. How should the two machines be connected?
Do i use the crossover lead an Ethernet lead or the wireless network?

Thanks once again for your patience.You should be able to use any kind of ethernet lead. But if you have wireless via a router that will definitely work cos I'm using just that now.

And with the greatest respect to my fellow posters you do not need filezilla > sudo apt-get --purge remove filezilla  to remove it from your system.

Follow my previous post and you should be good to go!

Mark

---

### Post by numbness05 on 2009-08-10
> **mapes12 said:**
> You should be able to use any kind of ethernet lead. But if you have wireless via a router that will definitely work cos I'm using just that now.

And with the greatest respect to my fellow posters you do not need filezilla  to remove it from your system.

Follow my previous post and you should be good to go!

Mark

ok filezilla is gone.

but I have followed your last post to the T over and over and still only seem to be able to access my desktop from my laptop and not visa versa as needed..

any idea what could be stopping me please mark??

thanks a million for all of your help so far

---

### Post by mapes12 on 2009-08-10
> **numbness05 said:**
> ok filezilla is gone.

but I have followed your last post to the T over and over and still only seem to be able to access my desktop from my laptop and not visa versa as needed..

any idea what could be stopping me please mark??

thanks a million for all of your help so farI'll give it a go.

How are the machines connected please? Is there a router or some thing between them or are they directly wired?

On both machines in Terminal ```
ifconfig
```and post the output here making sure you let us know which is laptop and which is desktop output.

Take it fom there.

---

### Post by LewRockwell on 2009-08-10
no tech or hobbyist should be without one of these!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

.

---

### Post by numbness05 on 2009-08-12
[QUOTE=mapes12;7764907]I'll give it a go.

How are the machines connected please? Is there a router or some thing between them or are they directly wired?

On both machines in Terminal ```
ifconfig
```and post the output here making sure you let us know which is laptop and which is desktop output.

Take it fom there.[/QU


Thanks a million but Was being silly all I need to do is to transfer files form one machine to another my brain was so frazzled that I hadn't realised which way round this process worked...

So all files are now safely on ym desktop thank you for the advice though very much appreciated.

---

### Post by stinger30au on 2009-08-12
forget all the ip and ssh and the rest

sudo apt-get install giver

no config or nufin, it does the lot and works like a charm

---

### Post by mapes12 on 2009-08-12
> **stinger30au said:**
> forget all the ip and ssh and the rest

sudo apt-get install giver

no config or nufin, it does the lot and works like a charmI've read the Google page and watched the video. It looks great. Just tried to install on my machine running 8.04 with: > sudo apt-get install giver
and i get this:> mark@ubuntu-desktop:~$ sudo apt-get install giver
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package giver
mark@ubuntu-desktop:~$I guess it's a software sources issue. What do I need to add to my sources.list for apt-get to install this please? It doesn't say on the Google Giver website?

---

### Post by unutbu on 2009-08-12
Here's a tip: you can find this out yourself by going to [http://packages.ubuntu.com](http://packages.ubuntu.com) and searching for the package "giver".
You'll find it in intrepid and newer versions of Ubuntu, but not in hardy.
[http://packages.ubuntu.com/intrepid/giver](http://packages.ubuntu.com/intrepid/giver)

---

### Post by mapes12 on 2009-08-12
> **unutbu said:**
> Here's a tip: you can find this out yourself by going to [http://packages.ubuntu.com](http://packages.ubuntu.com) and searching for the package "giver".
You'll find it in intrepid and newer versions of Ubuntu, but not in hardy.
[http://packages.ubuntu.com/intrepid/giver](http://packages.ubuntu.com/intrepid/giver)OK. So there is no package for hardy. Googled everywhere. Downloaded the source code tar.gz
Ran ./configure then hit the "dependency" wall of death. Last dependency I couldn't find is "avahi-sharp" (whatever that does?). About to give up on **GIVER** (excuse pun) unless anyone knows of a "point and click" to install it on Hardy?

---

### Post by lkraemer on 2009-08-14
mapes12,
Maybe Keryx would point out the dependency you are missing.

[http://keryxproject.org/download/](http://keryxproject.org/download/)

It is supposed to grab all the dependencies needed for install.

Haven't tried it myself.

This might be of help!
[http://ubuntuforums.org/showthread.php?t=494198](http://ubuntuforums.org/showthread.php?t=494198)

If you get a giver.deb made for 8.04.3 I would like a copy....Please!
(Ref: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall))

lk

---

