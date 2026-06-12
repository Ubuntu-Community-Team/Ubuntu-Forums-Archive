---
title: "No access to the internet - Ubuntu 16.04"
date: 2018-01-06
forum: Networking &amp; Wireless
---

### Post by michael239 on 2018-01-06
I have been trying to figure out what has gone wrong with my internet/network connection for many days now, but it stays a mystery. I am not a Ubuntu guru, more likely an advanced novice, so I hope I will be able to describe the problem.
When I start up my computer, Ubuntu (version 16.04 LTS) seems to load normally. The desktop appears and in the right upper corner is a status bar (??) showing the ‘up and down arrows’ icon, indicating that I am connected to the internet – as it has always done. Up to a few days ago that is.
I started Firefox and was presented with : “Hmm. We’re having trouble finding that site. We can’t connect to the server at [www.ixquick.com]("http://www.ixquick.com"). If that address is correct, here are three other things you can try : Try again later - Check your network connection …….”
I wanted to read my mail first and started Thunderbird only to get “Thunderbird failed to connect to the server ….”
Back to Firefox and tried several of my bookmarks. Same result.
Tried also the browser that comes with Ubuntu. Same result.
As the addresses are all correct and I’m not behind a firewall (I guess), it had to be a network connection thing. Without going into details yet (I can provide them when necessary), I did the following :
- Checked the connection information and all seems well. It is called “Wired connection 1”
- Disconnected and reconnected. No problem. Still the same errors.
- Edited the connection, but again all seems normal.
- Tried to add a new connection and set things manually. Connection was achieved, but still no traffic.
I did shut down and restart the computer several times over the last days. No result.

And then I had a final idea. I booted my computer using the install CD and choose Try Ubuntu. It loaded perfectly. It also established connection with the internet, again called ‘Wired connection 1’.
And Lo and Behold, Firefox and Thunderbird just work fine. Otherwise I wouldn’t be able to contact this forum, would I?
The connection’s settings are – or at least seem to be – exactly the same and it cannot possibly be a hardware problem – QED
So I think that the last time when the connection has worked and then when I shut down my computer, the Shut Down app (??) must have saved some instruction or error, preventing programs – apps to use the internet connection. Could this be a bug?
But I sure would like to get things back to normal.

---

### Post by chili555 on 2018-01-06
Can you ping? From the terminal:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```If the first succeeds, like this:```
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
```And the second one fails, like this:```
ping: www.ubuntu.com: Name or service not known
```Then you probably have a DNS problem. [https://en.wikipedia.org/wiki/Domain_Name_System](https://en.wikipedia.org/wiki/Domain_Name_System)

What does this tell us?```
sudo resolvconf -u

```The solution depends, of course, on the result of the command.

---

### Post by tokyobadger on 2018-01-06
**edit: come back to this after trying chili555's suggestions**
I had something similar after an upgrade from 16.10 to 17.04. I fixed it as follows:

edit /etc/systemd/resolved.conf
uncomment DNS and set to 8.8.8.8 
uncomment DNSSEC and set the flag to =off

It might be good to keep a copy of the original /etc/systemd/resolved.conf just in case
```
sudo cp /etc/systemd/resolved.conf /etc/systemd/resolved.conf.bak
```
Then check that the copy is there before trying any edits.

To restore the original
```
sudo mv /etc/systemd/resolved.conf.bak /etc/systemd/resolved.conf
```
**edit:** updated the code to include sudo (required) and restore instruction

---

### Post by michael239 on 2018-01-06
Thanks for the replies guys.
I will dig into it, but it will have to wait until tomorrow.
I'll keep you informed.

---

### Post by michael239 on 2018-01-07
[COLOR=#000000][FONT=Arial][SIZE=3]Chili555 : I did what you suggested and got the negative ping result with ping -c3 [www.ubuntu.com](www.ubuntu.com) as you expected[/SIZE][/FONT][/COLOR] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I then executed sudo resolvconf -u but that doesn&#8217;t give any result at all. All I got is the cursor.

[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] [/LEFT] [LEFT] [/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Tokyobadger : I haven&#8217;t changed anything in resolved.conf yet.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]1) I don&#8217;t know what &#8220;uncomment&#8221; means - silly still-novice &#8211; but I suppose it&#8217;s removing the #.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]2) &#8216;sudo resolvconf -u&#8217; not giving a result might be important.[/SIZE][/FONT][/COLOR]
[/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]3) I keep asking myself why there suddenly be this DNS problem where there was none before and why there is no problem when I&#8217;m running &#8216;Try Ubuntu&#8217;.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I just compared resolved.conf with it&#8217;s equal in Try Ubuntu and their content is exactly the same:[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3][Resolve][/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]#DNS=[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]#FallbackDNS=8.8.8.8 8.8.4.4 2001:4860:4860::8888 2001:4860:4860::8844[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]#Domains=[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]#LLMNR=yes[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]#DNSSEC=no[/SIZE][/FONT][/COLOR][/LEFT]

---

### Post by tokyobadger on 2018-01-07
I'm going to suggest you wait for Chili555 to reply but in response to your point (1) yes, removing the # from the start of a line means uncomment. Everyone starts as a beginner. 

One thing which occurred in the issue I had was that booting from the rescue kernel (advanced options under the grub menu) would allow internet access whilst the regular kernel would not. You might try that as it won't involve making any changes.

**edit:** for some background to what I faced [https://ubuntuforums.org/showthread.php?t=2347827&p=13588162#post13588162](https://ubuntuforums.org/showthread.php?t=2347827&p=13588162#post13588162)

---

### Post by michael239 on 2018-01-07
[COLOR=#000000][FONT=Arial][SIZE=3]I was indeed going to wait for Chili555's point of view.
But meanwhile I'm going to try booting in rescue mode and see what happens. That can't do any harm, can it? At least I hope ...
Thanks for the background reading tips.
[/SIZE]
[/FONT][/COLOR]

---

### Post by tokyobadger on 2018-01-07
Booting rescue/recovery mode will do no harm whatsoever, it's just another data point in the process of elimination to work out what the issue is (provided you don't alter any settings while in recovery mode).

---

### Post by michael239 on 2018-01-07
Here's me back in Try Ubuntu mode :o
Recovery mode.didn't enable access to internet sites or my mailbox either.
Perhaps best to wait for chili555 before fiddling with resolved.conf.

---

### Post by chili555 on 2018-01-07
Please try:

```
sudo dpkg-reconfigure resolvconf
```
and then reboot. Then report the result.

---

### Post by tokyobadger on 2018-01-07
Michael239, thanks for reporting back. Since you are not reproducing the scenario I experienced it is possibly a different issue.

The fact that the livecd (16.04 x86-64?) provides an environment in which you can get online, what you can take away is that 

- there are no issues with your router/hub/modem etc nor with your ISP
- there are no hardware issues
- there is an issue in the configuration files related to networking

I'd suggest that you prepare to provide computer hardware details, details of how you connect to the net (wired/wireless, home/work, router/modem, etc), output of your last update (/var/log/apt/history), maybe also the date and version of your livecd.

As Chili555 suggested, this is most likely a DNS issue and I suspect that while the resolved.conf files on the installed system and the livecd look the same, at the time 16.04 was released systemd was not "in charge" of DNS resolution but as systemd evolved in one of the updates this changed.

The suggestion I made in post #3 is a fix for DNS handling. The post has the code to you need to back up, edit and restore if you wanted to try while waiting for further advice.

---

### Post by michael239 on 2018-01-07
Sorry chili555, still the same result

---

### Post by michael239 on 2018-01-07
OK tokyobadger, just read your last post.
I will try to proceed as you suggest but that will take me some time.
That will be all for today however. I'll be back as soon as possible.

---

### Post by michael239 on 2018-01-08
Here we go again.
 
chili555 : I tried the reconfigure command again to make sure, but nothing has changed.
 
Tokyobadger: I tried to edit resolved.conf but couldn't save it. It's read only and I can't change its permissions because I'm not the owner. Strange ....

---

### Post by tokyobadger on 2018-01-08
You need to edit as sudo
```
sudo nano /etc/systemd/resolved.conf
```
Ctrl+x to save an close

---

### Post by michael239 on 2018-01-08
Will do when I'm back in the installed system.
I'm running the liveCD now - as you can guess.

---

### Post by tokyobadger on 2018-01-08
I'd go back to post 3 where you have the steps to make a back up as well as restore the original file

---

### Post by michael239 on 2018-01-09
Here&#8217;s me back using the live CD again. You can guess what that means.
- I ran sudo nano /etc/systemd/resolved.conf, made the changes and rebooted. The problem is still there.
- I restored the original resolved.conf, rebooted and just to make sure, ran sudo dpkg-reconfigure resolvconf once more. Nothing changed.

So what will be the next step, if there is one?

---

### Post by michael239 on 2018-01-17
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Hi .[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Sorry for the late follow up but I was out of the country (Belgium) for a week. However, I often checked the forum when I had the chance and as there have been no new developments, I suppose you’re waiting for the details Toyobadger asked for in post #11[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]1) Desktop connection to the internet : home, wired, through my provider’s modem and then a router. Ubuntu’s set-up named it ‘Wired Connection 1’. I already tried a connection without the router but that doesn’t change anything and again, the Live CD works fine.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]2) The live cd was created march 15, 2017 (ubuntu-16.04.2-desktop-amd64.iso)[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]3) The history.log itself dates from January 1 2018 but it’s completely empty. There is however hystory.log.1.gz from December 23, 2017.[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]4) Hardware : as mentioned in #11, that can’t be a problem, as everthing was working fine before and it still is when running the live CD[/SIZE][/FONT][/COLOR][/LEFT] [LEFT] [/LEFT]

---

### Post by Hadaka on 2018-01-17
Hi, from a working wired connection..live cd is ok..
please open a terminal and do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then do..
Please open a terminal...ctrl/alt/t then Copy and Paste .
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Then do..
```
cat wireless-info.txt | nc termbin.com 9999
``` 
This will have an output that looks this...
**[http://termbin.com/xxyy](http://termbin.com/xxyy)**  <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

---

### Post by michael239 on 2018-01-17
Hi Hadaka.
I just completed the update and your code. The result is :
[http://termbin.com/4gzf](http://termbin.com/4gzf)

I don't know if this is important, but I noticed some error messages flashing by during the process.

I have to leave now.
I'll be back tomorrow 01-18 from 14:00 (GMT +1)

---

### Post by Hadaka on 2018-01-18
Hi, since this was working before..try booting into an older kernel..
..to boot to an older kernel..
```
*Turn off the computer
*Turn the computer back on while pressing and holding down the SHIFT key
*The computer will boot into the grub recovery mode
*Down arrow to Older Linux Kernel versions..press Enter
*Down arrow to an older kernel and press enter
*The computer will boot to that older kernel
```
Let us know if you can now get online.
Thanks.

---

### Post by michael239 on 2018-01-19
[LEFT] HI.
I did as you asked, but the problem stays the same.
[/LEFT] [LEFT] I did first choose the &#8230;.4.10.0-42 option, then &#8230;.4.10.0-36. I also tried to run them in recovery mode to see if that would help.[/LEFT] [LEFT] Starting up these versions takes ages &#8211; up to 5 minutes. One really needs to be patient. I guess this is because they are trying to access the internet after they (seem to have) established connection, which obviously they can&#8217;t.[/LEFT]

---

### Post by flix3 on 2018-01-20
@michael239: I'm having (what I think it's) the same problem and I've partially solved it so far.

I've not read all the posts on this thread (sorry). But in short my problem is:
[LIST]
[*]I can connect to my router but not to the web.
[*]I'm on Ubuntu 16.04 LTS.
[*]All the other devices can connect to the internet (with the same parameters: nothing special).
[*]I can connect using an Ubuntu live DVD (version 17.10).
[/LIST]

What I've done so far to (partially) solve the problem:
[LIST]
[*]From a terminal in the live DVD, after you're connected, (you can open a terminal by typing "terminal" after pressing the dash/search button in the left frame), I've typed: "systemd-resolve --status" (without the quotes). The result was in two lines (DNS servers and DNS domain). I've written them down (although I've used only the first line).
[*]From a terminal in normal Ubuntu (not the live DVD) I've typed: "sudo gedit /etc/resolv.conf". Then in gedit I've seen that the nameserver was different than the one in the first line of the previous call. So I've modified it and saved the file resolv.config (CTRL+S).
[*]Then I've just reconnected to the wifi and it worked (and now I'm writing this to you)
[/LIST]

I knew it was a DNS problem because in a terminal "ping 8.8.8.8" worked, but "ping www.google.com" didn't work.

What is still to be done:
[LIST]
[*]/etc/resolv.conf is automatically generated by nework-manager. So probably on next reboot I'll have to re-edit the file again.
[/LIST]

Hope this helps... at least this partially solved MY situation...

---

### Post by michael239 on 2018-01-21
Hi Flix3
Sorry, but &#8220;sytemd-resolve --status&#8221; just gives &#8220;unrecognized option '--status' &#8220;
I don&#8217;t know anything about systemd but feeling a bit adventurous I tried some other &#8216;options&#8217; with status. Until I left &#8216;--&#8217; or &#8220;-&#8221; out altogether . This was the result :

ubuntu@ubuntu:~$ systemd-resolve status
status: resolve call failed: All attempts to contact name servers or networks failed

By the way: &#8216;Ctrl+Alt+T&#8217; launches a terminal as well.

---

### Post by flix3 on 2018-01-21
@michael239: "systemd-resolve --status" gives "unrecognized option '--status'" to me too, on Ubuntu 16.04 LTS, but it works on my Ubuntu 17.10** live DVD**.

In fact it must be done **from the live DVD once you're correctly connected**. 
If you use a version older then 17.10 (that does not support "systemd-resolve --status") , you can try one of the following instead:
"nmcli device show wlan0 | grep IP4.DNS" or
"nmcli device show eth0 | grep IP4.DNS"
and see if you get something like:
```
IP4.DNS[1]:                             192.168.x.x
```
(where x.x are specific numbers)

This is the address of the DNS server that the live DVD is using: you must copy it to "/etc/resolv.conf" in normal Ubuntu.

---

### Post by flix3 on 2018-01-21
I've just found that once a connection is present, you can get the DNS also from the GUI, by clicking on the wifi icon on the top-right on the screen, and choosing "Connection Information".

Under "IPv4" you can find "Primary DNS".

This way is much easier to see if the Live DVD and normal Ubuntu are using the same DNS or not.

In any case, as I've already written, editing /etc/resolv.conf is only a partial solution, because that file "should" be overwritten by the network-manager. 

When this happens is a mystery to me... 
I can modify existing connection parameters and reboot and that file stays the same... (the connection keeps working)

But this does not look a very robust solution to me...

---

### Post by michael239 on 2018-01-22
Hi Flix3
I have just downloaded 17.10. I was planning to that anyway.
As soon as I'm used to it and have some result I'll let you know.

---

### Post by flix3 on 2018-01-22
> I have just downloaded 17.10
**You don't need it!**

As I've written, you can easily check the **PRIMARY DNS** address from the wifi icon at the top-right of the screen, clicking on "**Connection Information**".

Thus, even if now you can use "systemd-resolve --status" it's useless...

---

### Post by michael239 on 2018-01-26
[LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Hi guys.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I fear I&#8217;ll have to throw in the towel. I really would like to keep using Linux/Ubuntu on this computer (as I don&#8217;t want to have anything to do with Windows anymore ) but it turns out the system isn&#8217;t as stable as it should be. I had a first go at it in 2014 and had to stop because of other instability issues and lack of time. However, I&#8217;m not going to give up &#8211; otherwise I wouldn&#8217;t have spent 2 weeks already on this problem. Re-installing 16.04 would have been the easier option for sure.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]This being said, here&#8217;s what happened over the last two days with the installed version:[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]- I wanted to print some documents and suddenly it couldn&#8217;t send anything to the printer. It asked me to check my printer configuration. The day before the printer worked just fine. I checked the configuration and couldn&#8217;t find anything wrong. I re-booted in recovery mode and was told the boot partition contained a file system with errors and to run fsck manually &#8211; which I did. Ubuntu started, but still wouldn&#8217;t print.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Yesterday I got another error message : &#8216;&#8230;. low graphics mode. Your screen, graphics card and input device settings could not be detected correctly. You need to configure these yourself&#8217;[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]What the h**ll is this? There is nothing wrong with my hardware. Everything &#8211; Internet, printer, screen - functions and runs fine from the Live CD &#8211; both 16.04 and 17.10.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I don&#8217;t want to spend more time on these problems. But I do have my suspicions about what&#8217;s going on: there must be a bug in the &#8216;Shut Down&#8217; module. I think it keeps some kind of record of various settings to be used when you re-boot. And sometimes it screws that record up, and from then on things go from bad to worse.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]I&#8217;m going to (try to) re-install 16.04 and install 17.10 on an USB drive. I hope that a certain Irishman keeps well away this time.[/SIZE][/FONT][/COLOR][/LEFT]
 [LEFT] [COLOR=#000000][FONT=Arial][SIZE=3]Many thanks to all who contributed to this thread.[/SIZE][/FONT][/COLOR]
[/LEFT]

---

