---
title: "Synaptic Package Manager won't connect."
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by museum_geek on 2006-08-21
Hi,

I can ping (e.g. ping ubuntu.com) and browse the Internet using Firefox.  I have disabled IPv6 in the browser.  

I have also disable IPv6 for all of the applications, thinking that it might have been the same problem.  However, I still can't use other applications.  For example, Gaim won't connect to the Internet.  More importantly, Synaptic Package Manager and other package updating apps won't connect to the Internet.

Thanks,

---

### Post by Dr. Nick on 2006-08-21
Do you have any proxies set? Look under System - Prefrences -Network Proxy and make sure it is on "direct connection" Also it may help to run 

sudo apt-get update

from the terminal and see if you can get a more specific error message about not connecting

---

### Post by museum_geek on 2006-08-22
I have checked and the "Directly connect to the Internet" is selected.

When I run things like:

sudo apt-get install build-essential (or something similar), it just freezes when trying to access the [http://.](http://.)...... etc

---

### Post by RurouniKenshinX on 2006-08-25
I have the exact same problem man, I am really starting to get frustrated with it, however I have been working on some other things.  I am pretty fine for now as long as firefox works, but any help from anyone here on how to fix this would be extremelty great.

---

### Post by filthyfrog on 2006-08-25
Same problem here.:-k

---

### Post by RurouniKenshinX on 2006-08-25
this is frustrating, but for now im fine as long as firefox works since i disabled ipv6, and disabling it on the computer itself doesn't fix the problem

---

### Post by Dr. Nick on 2006-08-25
I have no issues with gaim or synaptic, Do any of you have a router installed? I have one and am fine, but it may have something to do with dhcp or dns assignments. If possible try plugging directly into the modem and see if the problem persists

---

### Post by drtvasudevan on 2006-08-26
i struggled with this for a long time and finally it was resolved when i net searched an IP number for my service provider and used that.
now it updates well.
so far not heard any complaints from ISP.

---

### Post by RurouniKenshinX on 2006-08-26
can you rephrase that as it was poorly phrased and doesn't really help.

---

### Post by drtvasudevan on 2006-08-28
it is unlike going to the website itself and downloading the packages.
there are proxy issues involved when apt-get or synaptic wants to access.
so though you can connect to the site apt-get may not work.

the way it was resolved for me was to give another DNS server address.
that was the ip address of my ISP.
they dont give that to the customer.
the customer connects to the ISP like a networked pc.
they in turn fetch what is wanted.
this does not seem to be compatible with apt-get.

to make matters simple let me state this.
if you are connecting to net through dhcp or 192.168.1.1 as DNS address you might have problems with synaptic.
ask your ISP to give you another ip address and add it to DNS server address.
or search google for ip address of your service provider and use that.

all this may not be technically correct. but that works for me.
hope that helps.

---

### Post by handy on 2006-08-28
As **drtvasudevan** says, the workaround for this is to find your isp's DNS addresses, there are usually 2, & manually put them in the **Menu: System / Administration / Networking / DNS (tab)**.

The problem that I still have is that quite often I have to input the DNS addresses **again**. After 1 or just a few reboots...

Because Dapper drops them, real fast??

There was a way to fix this permanantly in Breezy, [see here]("http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router"), 2nd post by **python** fixed this problem for me.  This doesn't work for Dapper. :cry: 

Anyone know a way to solve this?  It seems to be a problem with Ubuntu (specifically Dapper) & certain router/modems.

**[Edit:]** *The way I get my ISP's DNS addresses is to look into the firmware in the modem with Firefox.  Most router's will let you do this, check in the manual  or on the website of the manufacturer for details, it's very easy to do.*

---

### Post by ludo88 on 2006-08-28
Hello,
Could you explain how you disabled ipv6 ?
thx

---

### Post by handy on 2006-08-28
I think I have found a way to solve this problem.

I will post tomorrow, with the details, after I have streamlined it to the best of my ability...;) 

Those of us who suffer from these rogue routers, should be able to have it taken care of for us automatically, every time we boot up... :KS

---

### Post by handy on 2006-08-28
> **ludo88 said:**
> Hello,
Could you explain how you disabled ipv6 ?
thx

It is all over the forums if you search for it...

But here we go anyway... ;) 

Enter **about:config** in the url field of firefox.

Then enter **ipv6** in the **Filter:** field of firefox.

Then double click on the only line showing in the firefox window, to change it's boolean value to **true**.

Close & re-open firefox & you should now have internet access! 

Enjoy! :KS

---

### Post by handy on 2006-08-29
[SEE THIS THREAD]("http://ubuntuforums.org/showthread.php?t=252967") for a much cleaner solution than my following hack?

**Success at last!!**

Many thanks to **huygens** for the sudo without password information! :cool: 

If you use the following instructions, what should happen, is that every time the computer boots up, it will copy the **resolve.conf** to **resolv.conf**, which when you check in the ***Menu:* System / Administration / Networking - DNS tab**, will have overwritten the wrong DNS number (the router's DNS number in my case 192.168.0.1) with your ISP's DNS number(s) so you can access the repositories.

As mentioned in previous posts, my router's gateway address keeps overwriting the ISP's DNS, when I reboot, not allways, but very often!?:confused: 

The following works for me, on 2 different machines so far.

**_Here we go:_**

Find your ISP's DNS addresses (usually 2 of them, either from your router if you have access with your browser, or phone your ISP or look on their web site for the info'). 

Make a file called **resolv*e*.conf** (*spelling intended*) & put the 2 lines in like so:

[B]nameserver 144.140.70.29
nameserver 144.140.70.16[/B]

Unless you use Telstra in Australia, your ISP's DNS numbers will be different.

Now save & copy this file as **/etc/resolv*e*.conf**

Now make a file called **copy_resolv.conf.sh** with the following in it:

[B]#!/bin/sh
cd /etc
sudo cp resolve.conf resolv.conf[/B]

Save it somewhere in your /home, perhaps /home/scripts/ & also make sure that it is **Executable**.

Next we remove the need for a password on the command **cp**

The **sudo configuration** file can only be edited with the following command:

**sudo visudo**

Add the following line, where ***username*** is the account that you have booted with's **username**:

***username* ALL=NOPASSWD: /bin/cp**

Now write the file **<ctrl>** + **o**.
Now exit visudo **<ctrl>** + **x**.

Now go to ***Menu:* System / Preferences / Sessions - Startup Programs** & **Add** then **Browse** for **copy_resolv.conf.sh** hit **OK** when you have found it.

That's it!  Automatic updates are now available without manual intervention, I can access what I could not before.  The repo's are allways available.

If you need to tighten up the little security hole made by removing the sudo password from cp ?  Then go to [post #3, on this page]("http://ubuntuforums.org/showthread.php?t=245618"), where you will find **huygens** 2nd solution, which takes a little more time, but is very clever! :KS

---

### Post by jayelif on 2006-08-29
Same problem here, the manager says no connection but i can access all network, web or even chat...its just that the icon manager is cross out....what is going on](*,)

---

### Post by handy on 2006-08-29
> **jayelif said:**
> Same problem here, the manager says no connection but i can access all network, web or even chat...its just that the icon manager is cross out....what is going on](*,)

Did you read ALL of this thread?

Have you tried manually inputing your ISP's DNS address's & testing if that solves it?

If so my fix above will sort you out!

If you don't want to do that, at least you know by manually puting the right addresses in you can access the repo's.

OR you can make it so you just manually hit an icon on the panel to do it auto-manually before you access repo's, whilst your waiting for a bug fix!

---

