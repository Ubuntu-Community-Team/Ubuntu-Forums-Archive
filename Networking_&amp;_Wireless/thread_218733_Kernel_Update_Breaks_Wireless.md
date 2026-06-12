---
title: "Kernel Update Breaks Wireless"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by Flame0001 on 2006-07-19
I've seen on my own computer, my girlfriend's laptop, and many other users on this forum where our wireless cards are recognized, were working previously, but the latest kernel update broke our cards. We can see the network connections that are available, but we cannot connect to them. They are enabled and configured properly, but the last kernel update seems to have borked them somehow.

If anyone has input on this subject, be it similar problems or a possible solution, I'd greatly appreciate it.

---

### Post by wieman01 on 2006-07-19
I have seen this before while updating from *.23 to *.25 in connection with the Truecrypt software. This was annoying because I had to reinstall it from scratch (luckily I could recover my files on the encrypted volume).  

But that said, there is a potential risk that an upgrade tempers with your current configuration so I decided NOT do upgrade my kernel from now on until it is really necessary.

Not sure what others have got to say.

---

### Post by zoot_ on 2006-07-19
I'm not certain that it's kernel related, though I stand to be corrected. I'm helping out with an Ubuntu laptop remotely and since the updates on Friday, the laptop's wireless connectivity has become unreliable and mostly unusable. The system is using NetworkManager (nm-applet).

For this exact reason (things breaking on updates on the same release!), I will stick with Slackware for my own systems. This is a rather disappointing experience considering that I've been encouraging folks moving from MS to Linux to try Ubuntu. Thorough testing prior to updates is clearly not occurring....

---

### Post by wieman01 on 2006-07-19
> **zoot_ said:**
> I'm not certain that it's kernel related, though I stand to be corrected. I'm helping out with an Ubuntu laptop remotely and since the updates on Friday, the laptop's wireless connectivity has become unreliable and mostly unusable. The system is using NetworkManager (nm-applet).

For this exact reason (things breaking on updates on the same release!), I will stick with Slackware for my own systems. This is a rather disappointing experience considering that I've been encouraging folks moving from MS to Linux to try Ubuntu. Thorough testing prior to updates is clearly not occurring....

Could this be related to the "ipv6" thing again? I have heard of similar issues a couple of times and a common solution appears to be to blacklist the "ipv6" module. Want to try that?

---

### Post by forkd on 2006-07-19
I too am looking for a solution to this problem.  Perhaps you can help me understand how to "blacklist ipv6" :( 

I have recommended Ubuntu to many people because of my own good experience but now I'm in kind of a hot seat because I haven't been able to fix the problem.  I sure would like to find a solution to this so I can save face. :)

---

### Post by Robor on 2006-07-19
> **Flame0001 said:**
> I've seen on my own computer, my girlfriend's laptop, and many other users on this forum where our wireless cards are recognized, were working previously, but the latest kernel update broke our cards. We can see the network connections that are available, but we cannot connect to them. They are enabled and configured properly, but the last kernel update seems to have borked them somehow.

If anyone has input on this subject, be it similar problems or a possible solution, I'd greatly appreciate it.
This happens to me all the time.  When I was running Breezy I would do kernel upgrades and everything always went smooth.  Then one time a kernel upgrade broke my wireless (Intel 2200).  From that point on all future kernel upgrades required me to reinstall the firmware, ieee80211, and driver.  I'm not sure if all 3 were required but I did all of them because I was using some 'HowTo' instructions on how to reinstall the Intel 2200.

Now I'm running Dapper and I believe I've done 2 or 3 kernel upgrades.  The first one or two went without issue.  The most recent one broke my wireless again and I haven't been able to get it working.  ](*,)  :mad:  I think it's pretty sad that a system update requires reinstalling hardware that was working perfectly.  I don't know why it happens and honestly I don't care.  It shouldn't.  Period.  I've gotta admit, the more things that happen like this the more I'm going to lean toward moving to Vista when it's released.  :-k

---

### Post by Flame0001 on 2006-07-19
Alright, it does seem that IPv6 does break wireless for some computers, and here's how to fix it (Thanks to SlowJet).
```

sudo gedit /etc/modprobe.d/aliases
```

Then scroll down to where you see alias net-pf-10. Comment out alias net-pf-10 ipv6, and add a few lines so it looks like this:

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
```

Save the file and restart your computer. This did it for me, and I hope the same works for everyone else! Good luck! :D

---

### Post by Robor on 2006-07-19
Thanks...  I tried it and I'll give it a try when I get home.  

I followed a HowTo on WPA & Network Manager from this forum as well.  Will report back on my success or (more likely) failure.  ;)

---

### Post by cstudent on 2006-07-19
The last kernel update borked the wireless on my laptop. Some investigating in Synaptic showed that the linux-restricted-modules package for the recent kernel version was not installed for some reason. I reinstalled linux-image-686 (the kernel I use), linux-image-2.6.15-26-686 (not sure of the legit name) and linux-resticted-modules for same. That did the trick for me.


cstudent

---

### Post by aosborn on 2006-07-19
> **Flame0001 said:**
> Alright, it does seem that IPv6 does break wireless for some computers, and here's how to fix it (Thanks to SlowJet).
```

sudo gedit /etc/modprobe.d/aliases
```

Then scroll down to where you see alias net-pf-10. Comment out alias net-pf-10 ipv6, and add a few lines so it looks like this:

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
```

Save the file and restart your computer. This did it for me, and I hope the same works for everyone else! Good luck! :D

Wonderful, thanks!  This seems to have worked for me too on my Dell Inspiron 6400.  I'll see if it sticks after a couple reboots... the wireless connection on this machine has worked twice before with Dapper, once right after install and once after re-entering the WEP key, but after that it stopped and I couldn't get it working again even after following a couple of other suggestions in the forums.

Here's what I did:

- followed instructions above to edit aliases
- saved file and restarted
- noticed that now, my "wifi" light was solid green rather than blinking once each second (good)
- however, I still didn't have a working network connection
- based on another post, I toggled the wireless card on and off a few times using the Dell wireless function key (Fn+F2)
- still didn't have a working network connection
- disabled and enabled the wireless network connection using System->Administration->Networking... but it still didn't seem to work, it took a looong time to come back.

Then, maybe 30-60 seconds after all that, I had a working connection.  So I'm not sure which steps above were necessary, but just wanted to post this in case it helps someone else.

---

### Post by wieman01 on 2006-07-19
> **forkd said:**
> I too am looking for a solution to this problem.  Perhaps you can help me understand how to "blacklist ipv6" :( 

I have recommended Ubuntu to many people because of my own good experience but now I'm in kind of a hot seat because I haven't been able to fix the problem.  I sure would like to find a solution to this so I can save face. :)

Seems you have just answered your own question. :-) Good job! Glad it worked. Did the trick for me as well when I had such issues.

---

### Post by wieman01 on 2006-07-19
Another way of speeding up your system is to reconfigure firefox by telling it NOT to use IPV6 either. This is what you have to do:

1. Enter "about:config" using the address field of Firefox.
2. Enter "ipv6" using the "filter" text field.
3. Right-click on the line that has just appeared ("network.dns.disableIPv6") and choose "toggle".
4. Restart Firefox.

This value of "network.dns.disableIPv6" must be "true" in order to have it disabled. 

Now Firefox should run like a dream.

---

### Post by unconquerable on 2006-07-20
I just ised both IPv6 blacklisting methods discussed above (thanks by the way).  It got firefox pages loading, website used to not load at all.  But now synaptic just sits there when I try to have it download updates, It can't get the files even started.

What to do?

---

### Post by Robor on 2006-07-20
My wireless was working last night when I got home.  Not sure if it was the ipv6 thing or reinstalling my ieee80211, firmware, and driver.  Like most things I do in Linux, I follow a HowTo and hope it works.  If not, I'm usually unable to understand why.

The odd thing is the HowTo I followed was to enable WPA/WPA2 and my router is using WEP but it still worked.  I looked in Network Manager and see no option for WPA/WPA2.  Obviously I'm still using WEP even though I tried getting WPA/WPA2.  :-?

---

### Post by Robor on 2006-07-20
> **wieman01 said:**
> Another way of speeding up your system is to reconfigure firefox by telling it NOT to use IPV6 either. This is what you have to do:

1. Enter "about:config" using the address field of Firefox.
2. Enter "ipv6" using the "filter" text field.
3. Right-click on the line that has just appeared ("network.dns.disableIPv6") and choose "toggle".
4. Restart Firefox.

This value of "network.dns.disableIPv6" must be "true" in order to have it disabled. 

Now Firefox should run like a dream.
I just did this and Firefox didn't load any quicker but browsing is definitely faster.  Thanks!  :mrgreen:

---

### Post by wieman01 on 2006-07-20
> **Robor said:**
> I just did this and Firefox didn't load any quicker but browsing is definitely faster.  Thanks!  :mrgreen:

Sorry, perhaps I should have highlighted that Firefox won't load any quicker at all. That's not the purpose. It's the browsing which becomes way more enjoyable. :-) Glad it worked.

---

### Post by wieman01 on 2006-07-20
> **unconquerable said:**
> I just ised both IPv6 blacklisting methods discussed above (thanks by the way).  It got firefox pages loading, website used to not load at all.  But now synaptic just sits there when I try to have it download updates, It can't get the files even started.

What to do?

Man, beats me. I have not had such a problem on my computer so I don't know how to fix that.

Can you check if the repository sources are still valid? 

> sudo gedit /etc/apt/sources.list

Perhaps that's your problem although it's strange that it should stop working out of a sudden.

---

### Post by khoda on 2006-07-24
> **Flame0001 said:**
> Alright, it does seem that IPv6 does break wireless for some computers, and here's how to fix it (Thanks to SlowJet).
```

sudo gedit /etc/modprobe.d/aliases
```

Then scroll down to where you see alias net-pf-10. Comment out alias net-pf-10 ipv6, and add a few lines so it looks like this:

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
```

Save the file and restart your computer. This did it for me, and I hope the same works for everyone else! Good luck! :D

First time user here. My internet is very slow (I am plugged in though, not wireless). I tired to follow these steps but the text editor comes up blank. nothing is in the alias file... any ideas?

---

### Post by wieman01 on 2006-07-24
Well, no idea what is happening here but this is what I'd try:

1. Open the directory using the file manager (Nautilus? I am a KDE user... don't know the name of the tool).

2. Go to the directory "/etc/modprobe.d/".

3. Search for the file aliases and open it with a text editor (gedit).

Is it really blank? I don't think so, right? The terminal sometimes opens "blank" files when the command line is pointing to a file that does not exist, hence it creates a NEW file.

Try this and perform the steps described again using the terminal(!) once again (you have to use the terminal because the file manager does not allow you - by default - to act as "root" and change files outside the home directory).

Let me know if this has helped.

---

### Post by khoda on 2006-07-25
That didn't do it...

---

### Post by Robor on 2006-07-28
My wireless worked the first night.  I ran Automatix again to get the latest software and that broke my wireless again.  I've been on the wire since then.  Just don't feel up to going through the reinstall right now.  I'm afraid when Vista comes out I'm going to dump my data from this Ubuntu install and switch back to Windows.  Ubuntu is a nice free alternative but it's a royal PITA to actually use.

---

### Post by Jerome36 on 2006-08-05
> **wieman01 said:**
> Another way of speeding up your system is to reconfigure firefox by telling it NOT to use IPV6 either. This is what you have to do:

Awesome!  I've had Ubuntu for a while now, but have only used it for certain things, and surfing the internet wasn't one of them, as it was too slow.  I had heard about disabling ipv6, but never got around to doing it.  I just did what you suggested, with Firefox, and now the webpages load almost as fast as they do on my Windows box.  Thanks!

---

