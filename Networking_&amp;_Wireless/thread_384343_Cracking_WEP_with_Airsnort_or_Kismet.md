---
title: "Cracking WEP with Airsnort or Kismet"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by ThinkBuntu on 2007-03-14
Does anyone here have experience using Airsnort or Kismet? I'd really like to get either working...I've apt-get'd both (built from source my last time around, but this is a different machine) but don't know where to go from here.

I get an error when I enter kismet into the shell. Airsnort, on the other hand, boots fine, but I don't know how to use it at all.

I'm running Edgy on a ThinkPad T41 with an Atheros card. This card was supported from the get-go and is working as normal with Gnome Network Manager.

---

### Post by chili555 on 2007-03-14
I am not a moderator, so these comments are mine and mine alone. Since cracking WEP is illegal in many (most) locales, you will not get many answers. 

```
less /usr/share/doc/kismet/README.gz
```

---

### Post by ThinkBuntu on 2007-03-14
Both programs are FOSS, well known in Linux, Windows, and even Mac Circles, and are certainly used out there. It's also illegal to do filesharing for certain files, but people in here certainly sound off about that. Likewise, a legitimate argument could be applied to cracking WEPs (forgot password?).

---

### Post by Fatjoint on 2007-03-14
> **chili555 said:**
> I am not a moderator, so these comments are mine and mine alone. Since cracking WEP is illegal in many (most) locales, you will not get many answers. 

```
less /usr/share/doc/kismet/README.gz
```



It's not illegal to crack your own access point.  

If you'd like to see some of these programs in action, visit a torrent search engine and search for "hacking videos".  There are videos showing these tools in action, using that and a little reading of the manuals for the programs, you should be able to derive their use.

---

### Post by spd106 on 2007-03-14
Does anyone still use airsnort?

I think aircrack-ng is where all the action is these days ([http://www.wirelessdefence.org/index.htm)](http://www.wirelessdefence.org/index.htm)). It works well with my Atheros card. There's a good intro video on irongeek's website, though he uses Auditor (now Backtrack) the tools are available on Ubuntu too.

You will probably want to get the latest madwifi driver from [http://madwifi.org](http://madwifi.org) and if you want to do packet injection you will need to search for a driver patch. Needless to say Backtrack has this already taken care of.

I suggest that you read through the madwifi site in order to become familiar with VAP interfaces.

(Incidentally, the madwifi-tools package has been backported, but it just hasn't been uploaded to the repo yet.)

---

### Post by ThinkBuntu on 2007-03-15
> **spd106 said:**
> Does anyone still use airsnort?

I think aircrack-ng is where all the action is these days ([http://www.wirelessdefence.org/index.htm)](http://www.wirelessdefence.org/index.htm)). It works well with my Atheros card. There's a good intro video on irongeek's website, though he uses Auditor (now Backtrack) the tools are available on Ubuntu too.

You will probably want to get the latest madwifi driver from [http://madwifi.org](http://madwifi.org) and if you want to do packet injection you will need to search for a driver patch. Needless to say Backtrack has this already taken care of.

I suggest that you read through the madwifi site in order to become familiar with VAP interfaces.

(Incidentally, the madwifi-tools package has been backported, but it just hasn't been uploaded to the repo yet.)
Good link. Thanks for the help! I noticed it says " WEP/WPA Cracking and Dictionary Attack Tools:" which seems promising because Airsnort and Kismet, as far as I know, are intended only for cracking WEP encryption.

---

