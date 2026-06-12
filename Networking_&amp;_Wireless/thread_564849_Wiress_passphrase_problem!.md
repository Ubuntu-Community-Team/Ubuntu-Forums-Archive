---
title: "Wiress passphrase problem!"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by meltedslush on 2007-10-01
Hey  guys,

I've been using Ubuntu for since this summer and I've been happy with this OS, until now.

Despite the fact that Ubuntu was my first Linux experience, I had fun with it, and figured just about everything out and made them work thanks to you guys and just searching on google.

So my problem is this:

My wireless works, unsecured wireless connection works, secured wireless connection works... only if its passphrase is in numbers. Well first, I couldn't get any secured wireless connection to work because I didn't know what all the ASCII and HEX, open and shared.. was, but after searching google for few days, I found out I can connect to internet by using WEP 128/64 HEX passphrase for my house and my friend's. However, when I went to my group member's house to work on a project, I could not do anything because I just couldn't get the password to work!

Everyone else got online. People with Mac OSX, Windows... except me. 

Felt pretty embarrassed, yes. I almost regretted changing to Ubuntu.

Her password was composed of letters and numbers, all being 13 characters. Hex didn't work for me this time, and neither did everythiing else. 

Is there no way ubuntu can understand alphabetized passwords?

Do i have to ask my friend to change the password just for me? I found a topic about you gotta actually open up router's set up system and find hex code... is that true?

I love Ubuntu, but this problem is a huge turn-off for me right now :(

---

### Post by MrFSL on 2007-10-01
As you can tell I'm sure from all of your searching, wireless issues are abundant in Ubuntu. The default (for Feisty) utility (i.e. Network Manager) leaves much to be desired. A good deal of your success is going to depend on which wireless adapter you have.

Personally I have an Intel 2200 BG. I get this information by doing:
```
lspci | grep -i wireless
```

This wireless chipset even have drivers already built into Ubuntu Feisty. However, it simply does not work with WPA. The issue is due to the WPA Supplicant driver. Network manager seems to be using the IPW driver (which it should but which doesn't work.) If I use the generic "wext" driver I have no problems. 

Now there is no easy way for me to force Network Manager to use this driver so I finally had no choice but to drop Network Manager in favor of another utility.

I have tried every wireless connection utility I could get my hands on and am currently using [wicd]("http://wicd.sourceforge.net/"). It has it's problems as a network connection / network settings utility, but as a wireless utility I can't complain. 

How I wish the people over at wicd would join forces with the Network-Manager/ Gnome Network-Manager group! One projects strengths is the other projects weakness!

To recap, I suggest using wicd for now.

---

### Post by meltedslush on 2007-10-01
Hey MrFSL,

Thanks alot for your information on Wicd! I was little scared switching wireless manager, but I did and well, I really like it!

I heard about Rutildt? I don't know if I spelled it right but it was suppose to be an another wireless manager, but yeah I definitely would prefer this over network-manager.

Truly, if Ubuntu can get wireless support straight, I'm sure many would choose this OS over windows anyday!

---

