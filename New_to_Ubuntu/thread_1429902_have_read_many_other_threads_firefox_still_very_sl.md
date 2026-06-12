---
title: "have read many other threads firefox still very slow"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-14
I've been reading and trying everything that seems relevant (and some some stuff that didn't seem relevant)  and I still can't figure out why firefox is so slow!  I decided to try another browser (epiphany) and that's slow too!!! I looked so make sure ip v 6 is disabled etc.  My other relevant info is mentioned in my signature.  Oh one more thing though I'm on a wireless network.  Firefox was not acting like this until about a day ago.  
brad@brad-laptop:~$ uname -r
2.6.31-20-generic
I just updated (my kernel) would that affect anything to do w/ my browsers??  My downloads are normal!!

---

### Post by chaanakya_chiraag on 2010-03-14
Hmmm...when did this start occurring?  Also, are you installing firefox from a launchpad/ppa repo or from the normal ubuntu repo?

---

### Post by bradmayne04 on 2010-03-14
i have not re-installed firefox. I'm using what came in w/ the install .iso disk.  Oh BTW I just rebooted into my old kernel and browser's are still acting slow.  Seems to be going slow on the "transfer".

brad@brad-laptop:~$ uname -r
2.6.31-14-generic
brad@brad-laptop:~$

---

### Post by Trandre on 2010-03-14
I had the same problem, ran top in terminal and both chrome and firefox where using 60 to 70 % of cpu.

I tried to roll back to the install moment, and deleted files in home. This fixed my browser issue but killed my service center. 

PS! I do not recommend my solution, but if you could do a safer roll back, it could help you. 

You can also run [http://www.pingtest.net/](http://www.pingtest.net/) if you want to rule out the quality of your network. 

Trandre

---

### Post by albert s on 2010-03-14
can you try a wired connection and see if that is slow too.

---

### Post by 2hot6ft2 on 2010-03-14
Here are a few things you can try.
Firefox changes

1) Type &#8220;about:config&#8221; (no quotes) in the address bar in the browser.
2) Copy and paste the Preference Name into the Filter
3) For true/false entries right click and select Toggle OR double click on it.
4) For others right click and select Modify
You might have to create some of these entries by Right Click &#8211;> New &#8211;>Interger or Boolean in the lower section where the preferences are.

```
Preference Name						Type		Value

config.trim_on_minimize				New ->	boolean		true
browser.blink_allowed					""		false
browser.urlbar.doubleClickSelectsAll			""		true
network.dns.disableIPv6					""		false
middlemouse.paste					""		true
browser.search.openintab				""		true
ui.submenuDelay					New ->	Integer		0
browser.sessionhistory.max_total_viewers		Integer		0 (was -1)
network.http.pipelining					boolean		true
network.http.proxy.pipelining				boolean		true
network.http.pipelining.maxrequests			Integer		some number like 10 (was 4)
nglayout.initialpaint.delay			New ->	Integer		0
content.notify.backoffcount				Integer		5
content.notify.interval				New ->	Integer		0

```
Close and reopen firefox.

What some of them do
Reduce RAM usage to 10mb when Firefox is minimized
config.trim_on_minimize

Reduce the amount of RAM Firefox uses for it&#8217;s cache feature
browser.sessionhistory.max_total_viewers

Increase the Speed in Which Firefox loads pages
network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

The amount of time the browser waits before it acts on information it receives.
nglayout.initialpaint.delay
-----
Change DNS Servers
Right click the network-manager applet in the top panel and select Edit Connections.
Select your wireless connection and click edit.
Under IPV4 add
> 208.67.220.220, 208.67.222.222
to the DNS Servers box.
Click Apply and Close
Restart networking
```
sudo /etc/init.d/networking restart
```
Or reboot.

Good luck.
You might also give swiftfox or opera a try.

---

### Post by bradmayne04 on 2010-03-14
what does "alias net-pf-10 off" do?  Why do i need different DNS numbers?  i looked at that and since I'm using DHCP so a lot of the area was "grayed out"  that area was shaded out.  Also I tried chaning the integers etc. that someone had mentioned and that was no good.  I went to pingtest.net and I got an "A" grade.  So there was no packet loss etc.  I'm running out of ideas here LOL.  Also it seems to happen no matter what browser i use so I'm not sure the browsers someone mentioned would make a difference at this point.  Like i said firefox was fine on another post firefox was working correctly until recently. Also all the other laptops and one desktop are running well.  This seems to be an isolated incident.  We just had a big storm over here in NJ and I thought that may have had something to do w/ it but no.  This is killing my will to live LOL!!!!

---

### Post by d3v1150m471c on 2010-03-14
Does your internet suck? Try using google chrome.

---

### Post by bradmayne04 on 2010-03-14
> **albert s said:**
> can you try a wired connection and see if that is slow too.

Yeah I'm on a wired ethernet connection going direct to my wireless router right now.  It's faster than it was.  Does that help narrow it down at all (I hope)??

---

### Post by richs-lxh on 2010-03-14
> **2hot6ft2 said:**
> 

Edit : ******************
Another option is in a terminal
Applications > Accessories > Terminal
use
```
gksu gedit /etc/modprobe.conf
```add the following command

alias net-pf-10 off                      

Save and close the file.

There is no modprobe.conf file in /etc/

That command to disable ipv6 used to be added to /etc/modprobe.d/aliases which also no longer exists.

Try adding it to /etc/modprobe.d/bad_list instead

[B]It's also possible to disable ipV6 from Grub at boot:
[/B]```
sudo nano /etc/default/grub
```And add this just before the "quiet splash" arguments:
```
ipv6.disable=1 
```So that it looks like this:
> GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”Then update Grub so that it gets added to /boot/grub/grub.cfg
```
sudo update-grub
```

---

### Post by bradmayne04 on 2010-03-14
So that alias is to disable ipv6??  I looked as though that was disabled when I right click on the network connection icon in the upper right of my GUI????  I am apprehensive about making any changes unless I understand them.  (no offense) 

> **richs-lxh said:**
> There is no modprobe.conf file in /etc/

That command to disable ipv6 used to be added to /etc/modprobe.d/aliases which also no longer exists.

Try adding it to /etc/modprobe.d/bad_list instead

---

### Post by richs-lxh on 2010-03-14
You are very right to not make changes unless you understand them. It's all so easy to just copy and paste commands from a forum, but not a good idea.

See my previous post (which I edited), you can also disable ipV6 from boot, the change is very easy to remove should it have no effect.

I think that the advice about changing your dns is a good idea, i use Vodafone as an isp and their dns servers are unreliable at best, so try that suggestion as well.

---

### Post by 2hot6ft2 on 2010-03-14
It's supposed to disable IPV6 but I have my doubts as to whether or not it actually works.
[http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/](http://www.ducea.com/2006/06/01/disable-ipv6-module-on-default-kernels/)

Found that suggestion in a few other places too.

---

### Post by bradmayne04 on 2010-03-14
how do i save in nano?  i'm not to familiar w/ it.  only used it once a few years ago.

---

### Post by 2hot6ft2 on 2010-03-14
I have removed it from the post since there seems to be a question as to it's usefulness. It seemed to help on mine but oh well. I think it was for when IPV6 was loaded as modules but since IPV6 is now part of the kernel I guess it's outdated. And was supposed to go in /etc/modprobe.d/aliases in the first place.

---

### Post by bradmayne04 on 2010-03-14
never mind i did it. and it's still slow LOL  arrrggggghhhhhh

---

### Post by 2hot6ft2 on 2010-03-14
> **bradmayne04 said:**
> never mind i did it. and it's still slow LOL  arrrggggghhhhhh
It wont effect anything in a negative way.
If everything else fails you might try using a windows driver in
System > Administration > Windows Wireless Drivers
which is ndiswrapper
```
sudo apt-get install ndiswrapper
```
if you don't have it.
You'll need the windows drivers .inf file for your wifi adapter to use it.
I'm not a fan of using windows drivers in linux myself but there's lots of info out there for those that want to try it.
I haven't used it either so I'll leave the ins and outs of setting it up, unloading and blocklisting the ubuntu drivers to those that have.

---

### Post by bradmayne04 on 2010-03-14
I just happened to look in my "warning" console on firefox.  There a a ton of errors:

Warning: Unknown property 'text-overflow'.  Declaration dropped.
Source File: [http://x.myspacecdn.com/modules/common/static/css/global_j9cbxmr0.css](http://x.myspacecdn.com/modules/common/static/css/global_j9cbxmr0.css)
Line: 1
Warning: Expected declaration but found '*'.  Skipped to next declaration.
Source File: [http://x.myspacecdn.com/modules/common/static/css/global_j9cbxmr0.css](http://x.myspacecdn.com/modules/common/static/css/global_j9cbxmr0.css)
Line: 1
Warning: Expected declaration but found '.'.  Skipped to next declaration.
Source File: [http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css](http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css)
Line: 1Warning: Expected declaration but found '.'.  Skipped to next declaration.
Source File: [http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css](http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css)
Line: 1Warning: Unknown property '-moz-opacity'.  Declaration dropped.
Source File: [http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css](http://x.myspacecdn.com/modules/common/static/css/uploadcontrol_ioe1imsn.css)
Line: 1
There are so many of them I would be here all night cuz I can't select all I'm going to do a couple screen shots that might be more time efficient in this case!!

What does this mean???????????????

---

### Post by richs-lxh on 2010-03-14
They mean "Don't ever use MySpace" Lol! :D

Try cleaning up Firefox cache and any other baggage. 
Tools > Clear Recent History

---

### Post by bradmayne04 on 2010-03-14
I already the wifi card working so i'm not sure I understand why I would want ndiswrapper.

> **2hot6ft2 said:**
> It wont effect anything in a negative way.
If everything else fails you might try using a windows driver in
System > Administration > Windows Wireless Drivers
which is ndiswrapper
```
sudo apt-get install ndiswrapper
```if you don't have it.
You'll need the windows drivers .inf file for your wifi adapter to use it.
I'm not a fan of using windows drivers in linux myself but there's lots of info out there for those that want to try it.
I haven't used it either so I'll leave the ins and outs of setting it up, unloading and blocklisting the ubuntu drivers to those that have.

---

### Post by 2hot6ft2 on 2010-03-14
> **bradmayne04 said:**
> I already the wifi card working so i'm not sure I understand why I would want ndiswrapper.
Me either.
To try and get it to go faster. Some people say that it's a lot faster with a windows driver but I'm like you. Like I said I'm not a fan of using windows drivers in ubuntu. There are those that will say right off the bat to either change to WICD or use ndiswrapper.

I would consider it a very last resort if I couldn't get it to work any other way. Just giving options. If speed is your only concern that is.

---

### Post by bradmayne04 on 2010-03-14
open DNS!!!!!!!!!!!!

So far, so good, so what.  -- Dave Mustaine (megadeth)

Thanks for everyone's input.  I really appreciate everyone lending a hand to the cause!!!!!!!!!

---

### Post by itismike on 2010-03-16
@bradmayne04 - It looks like you found a solution but I can't understand what the magic was.  Does "open DNS!!!!!" mean you changed your DNS settings and now it's working better?

---

### Post by sgosnell on 2010-03-16
Using OpenDNS is one of the better changes you can make.  It's faster, and you can set aliases, letting you type short entries into the address bar instead of long URLs.  Lots of other advantages too, listed on the OpenDNS website.

---

### Post by bradmayne04 on 2010-03-17
yeah i thought it was fixed now again tonight it's acting really really slow and pages are not even loading correctly at this point.  I am running out of ideas at this point.  How would I go about COMPLETLY removing firefox and reinstalling????

---

### Post by 2hot6ft2 on 2010-03-17
You can either search for firefox in synaptic and select completely remove.
Then reinstall it.
Or using a terminal
```
sudo apt-get purge firefox
```
that will completely remove it along with any configuration files. Then
```
sudo apt-get install firefox
```
to install it.

---

### Post by bodhi.zazen on 2010-03-17
Be careful with that command, firefox has a ton of dependencies.

My advise would be to try Icecat or firefox 3.7 (3.7 is in pre release).

both these browsers solved problems I was having with firefox 3.5.x as 3.6 (from mozilla).

[http://ftp.mozilla.org/pub/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/firefox/nightly/latest-trunk/)

[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)

---

### Post by bradmayne04 on 2010-03-17
All right I'm gonna give it a shot.  I think it's more than just firefox.  I say this because when I used ephihany I had the same prob!! I'm gonna give this a shot though.

---

### Post by bradmayne04 on 2010-03-17
> **bodhi.zazen said:**
> Be careful with that command, firefox has a ton of dependencies.
 
My advise would be to try Icecat or firefox 3.7 (3.7 is in pre release).
 
both these browsers solved problems I was having with firefox 3.5.x as 3.6 (from mozilla).
 
[http://ftp.mozilla.org/pub/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/firefox/nightly/latest-trunk/)
 
[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)
 
I just got done looking at the page.  UMMM that's a lot of different things on there do I have to get a tape archive and untar??? There's no easier way?? I'm not the best at the command line....

---

### Post by bodhi.zazen on 2010-03-17
Firefox is very easy to install directly and does not require the use of the command line.

Icecat is installed by adding a ppa and the instructions are on the page.

Honestly , IMO, it is not *that* difficult.

With firefox, download the archive to Desktop (does not matter) and 

```
sudo -i
cd ~your_ueser/Desktop
tar xvf firefox* -C /usr/local
```Run firefox with

/usr/local/firefox/firefox

you can update your launcher / menus.

Detailed instructions are here:

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

It includes information on an Ubuntu Firefox ppa if you wish, as easy as ice cat, and on that Mozilla site I count 3 lines of code

> cd ~
tar xjf firefox-*.tar.bz2[FONT=monospace]
[/FONT]~/firefox/firefox

Icecat is simply adding a ppa, it is 3 lines of code.

```
sudo add-apt-repository [B]ppa:gnuzilla-team/ppa
sudo apt-get update
sudo apt-get install icecat[/B]
```If you use the icecat ppa, icecat is in your menu, right next to firefox, lol

I am sorry you are frustrated, but, IMHO, it is not *that* hard to install icecat.

Certainly both options are on par with or easier then what you have done up to now.

---

### Post by bradmayne04 on 2010-03-17
> **2hot6ft2 said:**
> It wont effect anything in a negative way.
If everything else fails you might try using a windows driver in
System > Administration > Windows Wireless Drivers
which is ndiswrapper
```
sudo apt-get install ndiswrapper
```
if you don't have it.
You'll need the windows drivers .inf file for your wifi adapter to use it.
I'm not a fan of using windows drivers in linux myself but there's lots of info out there for those that want to try it.
I haven't used it either so I'll leave the ins and outs of setting it up, unloading and blocklisting the ubuntu drivers to those that have.
 
 
Hey does anyone feel like walking me through how to setup and use ndis wrapper???

---

### Post by bradmayne04 on 2010-03-17
Umm okay i got it install where can i find the inf file though??

---

### Post by 2hot6ft2 on 2010-03-17
What wifi adapter are you using? You'll need to find the windows driver for it.
If it's a usb adapter use
```
lsusb
```
in a terminal
if it's internal use
```
lspci
```
in a terminal
So we can see what you have and try and help find the driver.

---

### Post by bradmayne04 on 2010-03-18
> **2hot6ft2 said:**
> What wifi adapter are you using? You'll need to find the windows driver for it.
If it's a usb adapter use
```
lsusb
```in a terminal
if it's internal use
```
lspci
```in a terminal
So we can see what you have and try and help find the driver.

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Foxconn International, Inc. Device e01b
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d4600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

---

### Post by 2hot6ft2 on 2010-03-18
> **bradmayne04 said:**
> 04:00.0 Network controller: **Broadcom Corporation BCM4312 802.11b/g (rev 01)**

That is your wireless adapter the **Broadcom BCM4312 (rev 01)**
I'll look for your driver. Have you tried the guide for broadcom drivers that includes yours here?
[[SOLVED] The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by 2hot6ft2 on 2010-03-18
I don't suppose that's a HP Laptop, dv4 perhaps?
If it's a HP you can find the windows driver on their website like this page for the [Hp Pavilion dv4 - Model DV4T - 1400]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=3999441&lc=en&cc=us&dlc=en&lang=en&cc=us&submit=Go%20%C2%BB&y=6&x=4")
You can change the model from that page to yours if it's a HP. Then pick the windows OS that came on it and get the driver for either 32 bit or 64 bit whichever you're running in ubuntu. **If your signature is any indication "64 bit dual boot: 9.10 karmic koala" then you would want the 64 bit windows driver for windows 7**.

That's half the battle finding the windows driver.

For that matter if your windows 7 is 64 bit you should be able to browse to your broadcom folder on windows and copy the .inf file to ubuntu.

I'm calling it a night. I'll check your progress tomorrow.
G'night

---

### Post by bradmayne04 on 2010-03-18
> **2hot6ft2 said:**
> That is your wireless adapter the **Broadcom BCM4312 (rev 01)**
I'll look for your driver. Have you tried the guide for broadcom drivers that includes yours here?
[[SOLVED] The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

Yes i think you had posted the other day when I was saying that the driver I have works?  I'm not trying to be rude i am without a doubt always thankful for any positive help i receive here but like I said in a previous post that I have a wireless driver working.  How good the driver is working is debatable as i can not understand why for the life of me that firefox ver. Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8 and ALL and I repeat ALL other browsers are slow as molasses(only linux browsers! such as ephipany!!  Winblows browsing is fine even preferable at this point)  I even went back to a different kernel.  I am now using brad@brad-laptop:~$ uname -r
2.6.31-20-generic
I'm wondering if there's something in a config file somewhere??  I'm not really familiar enough w/ ubu or linux at all to figure it out but the internet is so slow w/ any browser w/ ubu.  I go to windows on the other partition and the net is fine!  I go to any other computer in my house and the net is fine!! I download something in ubu and it's FINE!! WHY IS EVERY BROWSER I RUN IN UBUNTU SO SLOW??????????  IT'S KILLING ME!!!  OH!! one more thing that's even more frustrating!  Until sunday there was no lag or slowdown while browsing!!

---

### Post by bradmayne04 on 2010-03-18
no I'm sorry but it's not an HP.  The make and model of my laptop are in my signature.

---

### Post by iurpas on 2010-03-18
ok...so this seems to be my thread too...I've been lost for a few days ( a week maybe?) with this. I think I read all the the posts I could but to no avail.. I've tried firefox (i'm currently with the pre-release namoroka), chrome, opera, epiphany and I experience the same thing all over again... 

with firefox it keeps "looking up..." for a long time until it loads the page... (and displays tons of error warnings on the console)
with chrome it keeps "resolving hosts"
with opera... its even slower(?!) and epiphany the same thing

so it's not the browser...

disabled Ipv6 (both in grub and firefox)
changed dns servers (used google's - it seemed better but it wasn't)
input the dns servers manually on system/preferences/network connections and on resolv.conf 
uninstalled and installed browsers (although didn't purge firefox yet...)
...and everything is the same...

I'm running a xp virtual machine in ubuntu and browsing with IE is fine
download speeds are fine but it takes longer to check links (with tucan for instance)
I get almost the same thing with wired and wireless connections

.. and some days ago everything was dandy... :) ... I'm getting really frustrated...

I configured samba to share files and a printer with a vista on my network (maybe made a mess somewhere?)

If I can contribute with info in any way please just say so...I think bradmayne's solution is probably mine too...

thanks 

rui

---

### Post by bradmayne04 on 2010-03-18
> **iurpas said:**
> ok...so this seems to be my thread too...I've been lost for a few days ( a week maybe?) with this. I think I read all the the posts I could but to no avail.. I've tried firefox (i'm currently with the pre-release namoroka), chrome, opera, epiphany and I experience the same thing all over again... 
 
with firefox it keeps "looking up..." for a long time until it loads the page... (and displays tons of error warnings on the console)
with chrome it keeps "resolving hosts"
with opera... its even slower(?!) and epiphany the same thing
 
so it's not the browser...
 
disabled Ipv6 (both in grub and firefox)
changed dns servers (used google's - it seemed better but it wasn't)
input the dns servers manually on system/preferences/network connections and on resolv.conf 
uninstalled and installed browsers (although didn't purge firefox yet...)
...and everything is the same...
 
I'm running a xp virtual machine in ubuntu and browsing with IE is fine
download speeds are fine but it takes longer to check links (with tucan for instance)
I get almost the same thing with wired and wireless connections
 
.. and some days ago everything was dandy... :) ... I'm getting really frustrated...
 
I configured samba to share files and a printer with a vista on my network (maybe made a mess somewhere?)
 
If I can contribute with info in any way please just say so...I think bradmayne's solution is probably mine too...
 
thanks 
 
rui
 
you know now that you mention samba.  That makes me think too.  i had to install winbind.  I think i made some other changes as well.  I wonder....

---

### Post by 2hot6ft2 on 2010-03-18
I was tired, sorry I missed the pc's info.

Found your driver on this page:
[http://www.emachines.com/support/drivers.html](http://www.emachines.com/support/drivers.html)

Here it is for win 7 Pro 64 bit
[Broadcom Wireless LAN Driver (4312) 5.60.18.8 - 16.3 MB  2009/10/23]("http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/Wireless%20LAN_Broadcom_5.60.18.8_W7x64W7x86_A.zip?acerid=633918976047124991&Step1=Notebook&Step2=E%20Series&Step3=E725&OS=711&LC=en&BC=eMachines&SC=PA_6E")

There is only one .inf file in it so that will be the one you want. It's **bcmwl6.inf** just extract it from the zip file to somewhere like your home folder. Then follow the help pages instructions for setting it up.

Since your ubuntu is 64 bit get the 64 bit driver.
And here is the ubuntu help page for configuring ndiswrapper
[WifiDocsDriverNdiswrapper]("http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I hope that helps you get it running right.

---

### Post by bradmayne04 on 2010-03-18
> **2hot6ft2 said:**
> I was tired, sorry I missed the pc's info.
 
Found your driver on this page:
[http://www.emachines.com/support/drivers.html](http://www.emachines.com/support/drivers.html)
 
Here it is for win 7 Pro 64 bit
[Broadcom Wireless LAN Driver (4312) 5.60.18.8 - 16.3 MB 2009/10/23]("http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/Wireless%20LAN_Broadcom_5.60.18.8_W7x64W7x86_A.zip?acerid=633918976047124991&Step1=Notebook&Step2=E%20Series&Step3=E725&OS=711&LC=en&BC=eMachines&SC=PA_6E")
 
There is only one .inf file in it so that will be the one you want. It's **bcmwl6.inf** just extract it from the zip file to somewhere like your home folder. Then follow the help pages instructions for setting it up.
 
Since your ubuntu is 64 bit get the 64 bit driver.
And here is the ubuntu help page for configuring ndiswrapper
[WifiDocsDriverNdiswrapper]("http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
 
I hope that helps you get it running right.
 
Okay cool.  I'm gonna try it a little later on tonight.  Thanks for the help!

---

### Post by 2hot6ft2 on 2010-03-18
Just came across a thread dedicated to your exact card. Thought you might be interested so here it is:
[HOWTO: Use b43 driver with 14e4:4315 (Broadcom bcm4312 rev 01)]("http://ubuntuforums.org/showthread.php?t=1266620")

And welcome

---

### Post by iurpas on 2010-03-18
ok..sorry to intrude...but i was having the same problem, removed windbind and everything went back to normal.

Obviously I have no idea why...but it worked

---

### Post by 2hot6ft2 on 2010-03-18
> **iurpas said:**
> ok..sorry to intrude...but i was having the same problem, removed windbind and everything went back to normal.

Obviously I have no idea why...but it worked
You're not intruding at all. You have an idea and it's worth looking into. That's winbind...
> **bradmayne04 said:**
> you know now that you mention samba.  That makes me think too.  i had to install winbind.  I think i made some other changes as well.  I wonder....
Here's the Synaptic info for winbind:
> Samba nameservice integration server

Samba is an implementation of the SMB/CIFS protocol for Unix systems,
providing support for cross-platform file and printer sharing with
Microsoft Windows, OS X, and other Unix systems.  Samba can also function
as an NT4-style domain controller, and can integrate with both NT4 domains
and Active Directory realms as a member server.

This package provides winbindd, a daemon which integrates authentication
and directory service (user/group lookup) mechanisms from a Windows
domain on a Linux system.  User/group lookups are configured via
/etc/nsswitch.conf, and authentication is integrated using the winbind
module for PAM.
I'm not using samba so I don't know if it's required for samba or not. I use SSH and FreeNX and don't have winbind installed.

Looks like you can stop winbind according to the [ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") using
```
sudo /etc/init.d/winbind stop
```
and to start it again use
```
sudo /etc/init.d/winbind start
```
to see if it helps.

---

### Post by hansdown on 2010-03-18
I suspect winbind can be ruled out, as I don't have winbind installed, and firefox 64 Bt, and google chrome 64 Bt, both have very s...l...o...w page loading.

If I install packages from synaptic, they fly.

Not sure why.

---

### Post by 2hot6ft2 on 2010-03-18
> **hansdown said:**
> I suspect winbind can be ruled out, as I don't have winbind installed, and firefox 64 Bt, and google chrome 64 Bt, both have very s...l...o...w page loading.

If I install packages from synaptic, they fly.

Not sure why.
Sure wish someone could figure out what the real culprit is. My wifi was slow some days and fast on others. I'm hard wired right now. Seemed to be doing good before I went wired though.

---

### Post by hansdown on 2010-03-18
> **2hot6ft2 said:**
> Sure wish someone could figure out what the real culprit is. My wifi was slow some days and fast on others. I'm hard wired right now. Seemed to be doing good before I went wired though.

I thought some help was coming from the high CPU usage of firefox, but it may be something different?

I'm hardwired, too.

I'm not very well informed on this, but my guesses would go toward; flash implementation, or perhaps, java?

---

### Post by 2hot6ft2 on 2010-03-18
> **hansdown said:**
> I thought some help was coming from the high CPU usage of firefox, but it may be something different?

I'm hardwired, too.

I'm not very well informed on this, but my guesses would go toward; flash implementation, or perhaps java?
No since I tried swiftfox, opera, chrome and epiphany browsers and it didn't change. Some didn't even have flash or java as far as I know. Besides I'm on firefox now and the cpu is only at 13% when changing pages.

---

### Post by hansdown on 2010-03-18
> **2hot6ft2 said:**
> No since I tried swiftfox, opera, chrome and epiphany browsers and it didn't change. Some didn't even have flash or java as far as I know.

Hmmm... Thanks 2hot6ft2.

My theories are not so useful.

What next?

There has to be a common denominator, beyond the obvious; 64 Bt.

---

### Post by 2hot6ft2 on 2010-03-18
> **hansdown said:**
> 
There has to be a common denominator, beyond the obvious; 64 Bt.
I run 32 bit. Like I said mine was doing good before switching the routers location so I could plug in. That was because I'm always fiddling with things and got tired of having to go to the other building to reset it when I threw a wrench in the settings.;)

The one that seemed to make the most noticeable change was
Change DNS Servers
Right click the network-manager applet in the top panel and select Edit Connections.
Select your wireless connection and click edit.
Under IPV4 add
> 208.67.220.220, 208.67.222.222
to the DNS Servers box.
Click Apply and Close
Restart networking
```
sudo /etc/init.d/networking restart
```
Or reboot.

---

### Post by hansdown on 2010-03-18
> **2hot6ft2 said:**
> I run 32 bit. Like I said mine was doing good before switching the routers location so I could plug in. That was because I'm always fiddling with things and got tired of having to go to the other building to reset it when I threw a wrench in the settings.;)

The one that seemed to make the most noticeable change was
Change DNS Servers
Right click the network-manager applet in the top panel and select Edit Connections.
Select your wireless connection and click edit.
Under IPV4 add

to the DNS Servers box.
Click Apply and Close
Restart networking
```
sudo /etc/init.d/networking restart
```
Or reboot.

Hmm... The only thing I did, was fresh install Karmic.

---

### Post by 2hot6ft2 on 2010-03-18
> **hansdown said:**
> Hmm... The only thing I did, was fresh install Karmic.
I've done so much to my system it's nothing even close to a fresh install... I've removed network manager installed wicd removed it and installed network manager and even disabled NM and ran without it trying to connect 2 ubuntu's by crossover cable while still using wifi for internet on both. The list goes on and on.

---

### Post by hansdown on 2010-03-18
> **2hot6ft2 said:**
> I've done so much to my system it's nothing even close to a fresh install... I've removed network manager installed wicd removed it and installed network manager and even disabled NM and ran without it trying to connect 2 ubuntu's by crossover cable while still using wifi for internet on both. The list goes on and on.

So... is Karmic the common denominator?

---

### Post by 2hot6ft2 on 2010-03-18
> **hansdown said:**
> So... is Karmic the common denominator?
I would have to agree with you there. But I don't know if I'll upgrade to Lucid, I may wait for 10.10 since I've done so many modifications.

---

### Post by bradmayne04 on 2010-03-19
well i removed winbind and everything is good.  I got a PM from someone today that had posted on this thread cuz he was having problems which were very similar to mine.  However now I obviously can't use samba!  I was wondering say I download winbind again.  Then how could I configure samba and winbind daemons to not start at boot??  Then i could start winbind and samba from a shell.  I'm thinking this could theoretically work as a temporary workaround??  However I'm not familiar enough w/ how to configure this so that it's disabled at boot.  Any idea's guys and gals??

---

### Post by 2hot6ft2 on 2010-03-19
> **bradmayne04 said:**
> well i removed winbind and everything is good.  I got a PM from someone today that had posted on this thread cuz he was having problems which were very similar to mine.  However now I obviously can't use samba!  I was wondering say I download winbind again.  Then how could I configure samba and winbind daemons to not start at boot??  Then i could start from a shell.  I'm thinking this could theoretically work as a temporary workaround??  However I'm not familiar enough w/ how to configure this so that it's disabled at boot.  Any idea's guys and gals??
Glad to hear it. I don't have winbind installed so I can't say for sure that it will be there but take a look in
System > Preferences > Startup Applications
and see if winbind and samba are there. If they are unchecking them should stop them from starting up when the pc does.
After unchecking them if they are there close Startup Applications then reopen it and make sure they're still unchecked.
I had to do it a few times to disable network manager a while back.

---

### Post by bradmayne04 on 2010-03-19
nah man it's not in startup programs.  However like i was saying before, I already removed winbind.  I looked for samba and that was not in the startup app's,  I was thinking that maybe there was a way to change it in grub?  Like in nano or something?  If someone has the knowledge to walk me through this it would be awesome!

---

### Post by iurpas on 2010-03-19
Well... on my end removing windbind didn't make that a difference (if any?) i can still share files (z:\\myfiles) and the printer with a vista box...good enough..all started when I didn't manage to access the vista box just because it was named CLÁUDIA-PC and not CLAUDIA-PC (damn "`" !) so I started trying out everything I could to get it to work...I ended up with a lot of things installed I probably didn't needed...

I tried do stop windbind as mentioned above..but that didn't work, things only got better when I removed it

this was definitely our problem (brad's and mine)...have you tried sharing some files  or the printer are you sure I doesn't work any more?

(i do too get the cpu management problem when running firefox..but i've never tweeked the thing)

rui

---

### Post by bradmayne04 on 2010-03-22
So does anyone have an idea about winbind and samba??  

> **iurpas said:**
> Well... on my end removing windbind didn't make that a difference (if any?) i can still share files (z:\\myfiles) and the printer with a vista box...good enough..all started when I didn't manage to access the vista box just because it was named CLÁUDIA-PC and not CLAUDIA-PC (damn "`" !) so I started trying out everything I could to get it to work...I ended up with a lot of things installed I probably didn't needed...

I tried do stop windbind as mentioned above..but that didn't work, things only got better when I removed it

this was definitely our problem (brad's and mine)...have you tried sharing some files  or the printer are you sure I doesn't work any more?

(i do too get the cpu management problem when running firefox..but i've never tweeked the thing)

rui

---

### Post by iurpas on 2010-03-24
[http://ubuntuforums.org/showthread.php?p=9018806](http://ubuntuforums.org/showthread.php?p=9018806)

as i wrote i the pm....just thought it might be good to post it here too..

hope it will help.

rui

---

