---
title: "wireless stopped working"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by vermouthbianco on 2011-03-28
hey guys.  here's the problem in list form for simplicity:

-my wireless has stopped working
-i cant pick up any signal for any wireless- usually i can see neighbors around me
-4 or 5 days ago it happened and i fixed it by pressing wireless key/function key 
-ive been using an ethernet cable since 
-someone suggested that whatever software (probably the wrong term- sorry)makes the wireless card work may need to be uninstalled and reinstalled but i don't have any idea how to do this.

i dont know how to use ubuntu that well so if you give advice please be gentle on me.

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> hey guys.  here's the problem in list form for simplicity:

-my wireless has stopped working
-i cant pick up any signal for any wireless- usually i can see neighbors around me
-4 or 5 days ago it happened and i fixed it by pressing wireless key/function key 
-ive been using an ethernet cable since 
-someone suggested that whatever software (probably the wrong term- sorry)makes the wireless card work may need to be uninstalled and reinstalled but i don't have any idea how to do this.

i dont know how to use ubuntu that well so if you give advice please be gentle on me.

Before going to that level can you go to the terminal (applications>>accessories>>terminal) and copy/paste the output of 

```
rfkill list
```

back here. 
If you don't get an output then try the following to add the rfkill command

```
sudo apt-get install rfkill
```

then try rfkill list again. Note that the second command requires your password, which will not be echoed to the screen--not even *! Just put in your password and press enter.

---

### Post by vermouthbianco on 2011-03-28
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

this is what happened.  what does hard blocked mean?

---

### Post by KL_72_TR on 2011-03-28
Hello. I hope this could help to.
1 - Wireless signal is a radio signal. For this reason try to change the place of your device (the metallic structure in your building sometime can stand in the way).
2 - Consider the fact to upgrade to a newer version of Ubuntu: 10.04 or 10.10. It may be a bug problem and maybe it is solved in a new version.

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> 0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

this is what happened.  what does hard blocked mean?



Hard blocked means the wireless switch is in the off position. Try to move it and repeat the command and see if it changes the output.

---

### Post by vermouthbianco on 2011-03-28
I've done that many times, restarted computer and did it, etc.  It's a button on my computer.  so i did it again and entered the code in the terminal and nothing changes.....

(thanks for the help so far :) )

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> I've done that many times, restarted computer and did it, etc.  I've been doing that for days.  nada.



Dells sometimes have problem reading the switch. Try, copy/paste the following to the terminal.


```
sudo rmmod -f dell-laptop
```


If this works (it is just temporary) we will make it permanent. It will cause no other problems.

---

### Post by vermouthbianco on 2011-03-28
so i did that and this came up:


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

does that mean it worked because the first part isn't there anymore?  or should i restart my computer to see if it worked?  ...what does 'worked' mean? ;)

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> so i did that and this came up:


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

does that mean it worked because the first part isn't there anymore?  or should i restart my computer to see if it worked?  ...what does 'worked' mean? ;)



If it had worked it would have said  hard blocked: no
Rebooting would make the last command we tried disappear. So before we try that try.

```
sudo rfkill unblock all
```

---

### Post by vermouthbianco on 2011-03-28
nothing happened with that.  or i mean, it just came back with the original prompt.

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> nothing happened with that.  or i mean, it just came back with the original prompt.



Did you look at rfkill list again?

---

### Post by vermouthbianco on 2011-03-28
oh right.  okay its the same.


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> oh right.  okay its the same.


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes



I'm sorry but I am fresh out of ideas.  Perhaps the button itself finally gave up. I assume that you did not go into the bios and turn it off earlier-right!? Nothing we did will  be permanent after a reboot, but right now, I can't think of anything else but will continue to look at any other options or perhaps someone else more knowledgeable than me has another idea. Sorry.

---

### Post by vermouthbianco on 2011-03-28
well thank you so much for trying! :)

anyone else want to take a stab?  please!  thanks!

---

### Post by bkratz on 2011-03-28
> **vermouthbianco said:**
> well thank you so much for trying! :)

anyone else want to take a stab?  please!  thanks!



I did just find an entry on the web. Don't know how successful it was, but this is what I found.....


Quote
```
I also read, that some people could fix it, by turning off the WiFi button during the boot process and then switch it on again, once the system is up and running. It seems that the system expects the hard block to be set to off. This is still a bug, but it could explain why then the soft block didn't sync with the hard block any more.

```

Can't hurt to try.  Still looking

---

### Post by matt_symes on 2011-03-28
Hi

Open a terminal and type

```
sudo rfkill unblock wifi
```

Does that fix it ?

Kind regards

---

### Post by vermouthbianco on 2011-03-29
okay so i tried what you said, matt_symes.  it doesn't seem to do anything.

any other ideas?  i'm at a point where i think i should either upgrade to lynx or replace my wireless card.  i just don't get it.

---

### Post by matt_symes on 2011-03-29
Hi

Here is another technique that has worked for some people. This, of course, assumes it's a software issue and not a hardware issue like a stuck kill switch.

Open a terminal and type

```
sudo rm /dev/rfkill
sudo shutdown -r now
```

Maybe you will have more luck with that.

Kind regards

---

### Post by vermouthbianco on 2011-03-29
okay tried that.  it didn't do anything but surprise the hell out of me by suddenly rebooting.  

what about it being a hardware issue then?  what are solutions for that problem?

---

### Post by matt_symes on 2011-03-29
Hi

Hmmm. Sorry about the reboot shock :D That was the sudo shutdown -r now command. It idea is to recreate the /dev/rfkill device when rebooting.

I am beginning to wonder if this is not a hardware issue after all the software fixes you have tried.

What is the exact make and model of your laptop/PC ? That would be a good starting point.

Kind regards

---

### Post by Niedzwiedz on 2011-03-29
I was just here reading and killing some time waiting for a friend to come checkout my Linux on the HP.
I did a quick search and so warn this something on the internet!
Maybe some others helping can give this a read and see if it may be worth a try?
Down in the comments section there some it not work for them!
[http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/](http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/)

---

### Post by vermouthbianco on 2011-03-29
@ matt_symes

my computer is a dell inspiron 1545.  ive had it for several years with a couple different versions of ubuntu on it. (always ubuntu)  and ive always been able to pick up wireless everywhere.  different countries, etc.  i have had internet here in this place for several months and it worked fine until randomly about a week ago.  i hadn't done the ubuntu updates or anything.  there's nothing i can figure except that the physical mechanism stopped working.  but i don't know how probable that is or what to do about it.

what do you think?

thank you for the attention :)  im so lost with this stuff!

---

### Post by Niedzwiedz on 2011-03-29
> **vermouthbianco said:**
> there's nothing i can figure except that the physical mechanism stopped working.  but i don't know how probable that is or what to do about it.

what do you think?

I may be wrong, but what has me curious is;
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

It seems to me it software, or this should be able to change to;
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

Then if it your hardware, it would still not work?

---

### Post by cmcanulty on 2011-03-29
I spent 2 hours yesterday with a dell that wouldn't connect to wireless. I finally went to the software center and downloaded some wireless tools and voila it worked, that was on a Inspiron 9300 laptop I don't have the machine home with me but search for linux wireless tools on google.I had the driver already and it worked fine until maverick upgrade but one of the tools worked after I tried several

---

### Post by matt_symes on 2011-03-29
Hi

> **vermouthbianco said:**
> @ matt_symes

my computer is a dell inspiron 1545.  ive had it for several years with a couple different versions of ubuntu on it. (always ubuntu)  and ive always been able to pick up wireless everywhere.  different countries, etc.  i have had internet here in this place for several months and it worked fine until randomly about a week ago.  i hadn't done the ubuntu updates or anything.  there's nothing i can figure except that the physical mechanism stopped working.  but i don't know how probable that is or what to do about it.

what do you think?

thank you for the attention :)  im so lost with this stuff!

It's hard to say if it's software or hardware as, in the past, there have been software bugs raised about hard blocked wireless adaptors.

Try running from a live CD/USB. See if it's still blocked. Also try with a different distro's live CD/USB and check that way.

That would be my first port of call. If it is blocked with the  LiveCD and another distro's CD, i would suggest the weight of evidence building for a hardware issue. 

It might also be worth unloading and reloading the kernel drivers to see if that changes anything. (Unlightly but you never know)

Please post the output of (case sensitive)

```
lspci -k | grep -A3 Wire
```

Kind regards

---

### Post by matt_symes on 2011-03-29
Hi

> **cmcanulty said:**
> I spent 2 hours yesterday with a dell that wouldn't connect to wireless. I finally went to the software center and downloaded some wireless tools and voila it worked, that was on a Inspiron 9300 laptop I don't have the machine home with me but search for linux wireless tools on google.I had the driver already and it worked fine until maverick upgrade but one of the tools worked after I tried several

Was the laptop hard blocked ?

Kind regards

---

### Post by matt_symes on 2011-03-29
Hi

@Niedzwiedz. At the moment all of us here who have helped are trying to find out why the wireless card is hard blocked. This seems to be the problem.

Kind regards

---

