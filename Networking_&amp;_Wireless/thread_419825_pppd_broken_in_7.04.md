---
title: "pppd broken in 7.04"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by mainely_linux on 2007-04-23
Greetings, I have a rather bizarre problem which I encountered while Feisty Fawn was still in testing.  I thought I would check out Feisty Fawn a few month ago, and everything worked ok except for my dial-up.  I could get connected without issue, but the moment I initiated any serious traffic (pop3, http) the connection would drop - pppd dies with exit code 16.  I thought, ok, this is still in testing so its probably not ready for prime time yet.  I re-loaded my laptop with 6.10 and my dial-up worked again as it always had.

I was excited when 7.04 was considered stable and released last week so I quickly upgraded without even thinking of that previous issue.  I use a wireless connection at work, so it wasn't until I got home that the dial-up issue reared its head again.

The same behavior takes place.  Checking my email, or trying to surf causes the connection to drop.  I can let the connection idle indefinitely and it stays active.  The moment I attempt any serious traffic it drops.  The wvdial and /var/log/messages output dont tell me much, but follow:

--> Connect time 0.3 minutes.
--> pppd: &#65533;[08][06][08]([11][06][08]
--> pppd: &#65533;[08][06][08]([11][06][08]
--> pppd: &#65533;[08][06][08]([11][06][08]
--> Disconnecting at Mon Apr 23 07:13:42 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

Apr 23 07:13:42 meridian pppd[5772]: Modem hangup
Apr 23 07:13:42 meridian pppd[5772]: Connect time 0.3 minutes.
Apr 23 07:13:42 meridian pppd[5772]: Sent 1248 bytes, received 7574 bytes.
Apr 23 07:13:42 meridian pppd[5772]: Connection terminated.
Apr 23 07:13:42 meridian pppd[5772]: Exit.

I have 2 work arounds which are unacceptable:

1) ssh to a remote box and run fetchmail against my work email server, run mutt in a small window (starting it up in a larger terminal causes too much traffic - pppd death).

2) setting up roommates wintendo machine to share dialup connection into wireless router, getting on the internet via router.

I poked around a bit and found a suggestion about commenting the "auth" section in /etc/ppp/options and creating a clean /etc/resolv.conf before connecting.  I'll try that tonight when I get home from work.  

Does anyone have suggestions about why this might be hapenning?  I tried downgrading ppp and also wvdial, which didnt solve the issue.  Perhaps its kernel related?

Thanks in advance for any assistance with this.

---

### Post by brucealeg on 2007-04-23
I don't think I am having the exact same issue as you, but it's very close. I am using a Verizon Wireless EVDO card via dialup. The new version actually sees the hardware and has set it up for me. All I had to do was tell the dialer to use this phone number, user name and /dev/ttyUSB0. 

Anyhow, 
I connect fine and experience really good speeds, but the connection only stays up for about 1-2 minutes and then it drops and has to recall.

The /var/logs/messages says an echo failed 4 times, so the serial connection must be down. It then redials and gets me back on. I'm also wondering if something is wrong with pppd.

Bruce

---

### Post by mainely_linux on 2007-04-23
Just an update, I tried the noauth and clearing out the /etc/resolve.conf tip.  It did not solve the problem.

I'm beginning to think its kernel related.

Any mods/users have ideas on a fix?

Thank you

---

### Post by mainely_linux on 2007-04-23
It seems the problem here is definitely related to the kernel.  Since I am one of 5 people on earth still using a modem to connect I doubt this issue will be given much priority.

The resolution in this case is to use kernel 2.6.17-10-generic.  I can connect fine with this kernel, pppd doesn't die upon network traffic.

---

### Post by Michl on 2007-05-03
> **mainely_linux said:**
> Just an update, I tried the noauth and clearing out the /etc/resolve.conf tip.  It did not solve the problem.


For what it is worth, the modem still works in edgy if you use wvdial. 

Someone should file a bug for the new Feisty problem.

Michael

---

### Post by mainely_linux on 2007-05-04
> **Michl said:**
> For what it is worth, the modem still works in edgy if you use wvdial. 

Someone should file a bug for the new Feisty problem.

Michael

Yeah, its not really a Feisty problem though, its kernel related.  I know I could have re-installed to get edgy working but my back-up process was too involved.  If you install kernel-2.6.17-10-generic you can use your modem fine in Feisty.

---

### Post by Michl on 2007-05-05
> **mainely_linux said:**
> Yeah, its not really a Feisty problem though, its kernel related.  I know I could have re-installed to get edgy working but my back-up process was too involved.  If you install kernel-2.6.17-10-generic you can use your modem fine in Feisty.

What about 2.6.17.11?

---

### Post by mainely_linux on 2007-05-06
I think I tried it, but vaguely recall I had trouble with something (not necessarily the modem) - sorry I cant be more help here.

If you can get a wired/wireless broadband connection somewhere - just download them both and test it out.

---

### Post by Michl on 2007-05-08
It turns out that the Edgy I am using with a modem (successfully) is
17-11.  But I guess I shouldn't assume that just because I am
using it without major problems in Edgy that it will run without major
problems in Feisty, or?

I download anything over 250 MB at work on a network connection.
But under that works in my home office.  I download over night or
while I am at work without a hitch.

M

---

### Post by raydar on 2007-05-15
Wow, I thought it was just me--you say your modem worked in wvdial but not otherwise?  

Both for the first time, I'm running Kubuntu and trying to set up a modem (for an AOL user, no less).  I've run Ubuntu on my own machine since just before Edgy, but never with a modem.  I have no working external modem, and I spent a week with one PCI Winmodem and one ISA hardware modem way down at the far end of my computer before I finally got hold of a PCI hardware modem, moved it to the first PCI slot 'cause I was tired of going through higher numbers in the KPPP config box, and finally got a successful modem detection for the first time ever.  (No /dev/modem has been created yet, but I wonder if a symlink I created for the Winmodem, etc., might've been a shot in my own foot.)

So now I read about wvmodem, in one of the scanModem documents, try it, and actually connected to my ISP.  I couldn't get PPP working, just text menus etc., but I about did a flip.  Couldn't get AOL to accept the correct uname & p/w for some reason, though.  I still cannot get KPPP to dial the modem or audibly take it off the hook, although modem queries in KPPP consistently succeed.  What doesn't KPPP like about my setup?

So I finally just typed sudo pppd at a prompt and got about ten lines of gibberish, which must be what's output as KPPP is sitting there with a blank output window for several seconds before it silently crashes and disappears.

I apologize for the excessive detail, but after a week, I'm willing to go to any length! :]    Has a solution been found?


[ The final /var/log/messages output for sudo pppd is as follows: ]

PPP generic driver version 2.4.2
pppd 2.4.4 started by root, uid 0
Using interface ppp0
Connect: ppp0 <--> dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Exit.

---

### Post by mainely_linux on 2007-05-16
> **raydar said:**
> Wow, I thought it was just me--you say your modem worked in wvdial but not otherwise? 

I have no experience connecting to AOL with linux.  It can probably be done though, AOL is a problem in itself if you ask me :) .  You said you got your modem to connect with the wvmodem tool?  What device did it use/detect?

To make your symlink, you just simple use that device in the following:

sudo rm /dev/modem
sudo ln -s /dev/ttyS?? /dev/modem

You may use wvdialconf & wvdial , check it out.

The problem in this thread is that the default feisty kernel breaks pppd and that the solution is to use 2.6.17-10 in its stead.  You may need to look elsewhere for your troubles.  It does sound like your modem will work fine, and you can do more flips :)

---

### Post by myii on 2007-05-26
Had a similar problem of dropped connections until I followed some of the advice I found here:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Of particular interest was the following section:

> 
If you lose the connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:

gksudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a '#' at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4.


Hope that comes in useful.

---

