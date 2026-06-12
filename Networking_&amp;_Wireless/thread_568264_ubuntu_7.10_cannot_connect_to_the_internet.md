---
title: "ubuntu 7.10 cannot connect to the internet"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by K-a-M-u-Z-u on 2007-10-05
i have upgraded my feisty to gutsy, but it wont connect to the internet.
when i do IWCONFIG it show that its conected(and i can login to my wireless router), but i cannot connect to the net.
i have also tried WIRED connection using PPPOECONF....
any suggestion?

---

### Post by El Rogueo on 2007-10-05
> **K-a-M-u-Z-u said:**
> i have upgraded my feisty to gutsy, but it wont connect to the internet.
when i do IWCONFIG it show that its conected(and i can login to my wireless router), but i cannot connect to the net.
i have also tried WIRED connection using PPPOECONF....
any suggestion?

I wasn't aware Gutsy was out yet, and if it's not then the generic answer to your problems is to just roll back to Feisty and wait for Gutsy to release completely.

when you tried the wired connection did it work?

Is the router itself preventing you from receiving incoming information?

Any sort of problems like this in Feisty?

thanks

---

### Post by K-a-M-u-Z-u on 2007-10-06
u used the "update-manager -d" to upgrade to the beta release of 7.10
i tried wired connection:
> i have also tried WIRED connection using PPPOECONF....
in feisty just before the upgrade the internet worked fine.
on XP the internet is working great(so the router is OK - the problem is only in ubuntu 7.10)

> the generic answer to your problems is to just roll back to Feisty
how do i do that?

---

### Post by El Rogueo on 2007-10-06
I can't find the thread that talked about rolling back distributions, unfortunately, so I'll have to keep looking. Does your GRUB list all of your kernel versions when you get the option to start ubuntu? You might be able to cheat it and boot into an earlier one than the newest one you have, but I'm not really sure :confused:

Gutsy comes out in something like 12 days, so you could just wait until then and upgrade to the officially stable version.

I'll keep hunting and post back later.

---

### Post by El Rogueo on 2007-10-06
Looks like all of the "roll back" options are actually cheats involving making an image of your harddrive beforehand and then just copying that back over if a problem occurs

It also appears that upgrade-manager has had problems in the past and that apt-get dist-upgrade is the safer way to go... if it lets you you might be able to give it a go and try to re-upgrade and see if the problem fixes. Then again, it appears to be a matter of internal admin dispute as to which is better, so I'm not sure how successful that will be...

The fact you can login to your router is the strangest part- most of the information on the net suggests that if you can do that much you should be able to connect to the internet also.


Here's some things that worked for other people with similar problems: [http://ubuntuforums.org/showthread.php?t=309134](http://ubuntuforums.org/showthread.php?t=309134)

more on that train of thought: [http://ubuntuforums.org/showthread.php?t=307758](http://ubuntuforums.org/showthread.php?t=307758)

some stuff in here might apply, what with how-tos and bug reports [http://ubuntuforums.org/showthread.php?t=511754&highlight=cannot+connect+internet&page=3](http://ubuntuforums.org/showthread.php?t=511754&highlight=cannot+connect+internet&page=3)

"**GUTSY GIBBON SHOULD NOT BE USED FOR YOUR DESKTOP UNTIL RELEASE IN OCTOBER 2007**
If you decide to use Gutsy Gibbon then you are doing it on your own risk and with the risk of major breakage and possibly losing data." There's one reason you're not getting much help from anyone else ](*,)

The Gutsy forum looks like there's just serious hardware incompatibilities, that's a huge thing right there that you won't be able to fix easily.

I think your best bet is to boot into an older kernel, that works pretty consistently.

---

### Post by K-a-M-u-Z-u on 2007-10-20
ok.i have upgraded ubuntu to 7.10 using the alternate cd, still no internet
i tried to put my ISP DNS serveres in the Network applets under DNS.
but still no internet
i tryed using DIRECT CONNECT to the router(insted the WIRELESS), configured PPPOECONF, but still...no internet...
what can i do? :confused:

---

### Post by mshaheen on 2007-10-20
i have wired internet connection and i had the same problem but it's fixed after doing the following 

1- in firefox type " about:config " in the address bar and hit enter 
2- search for IPV
3- change " network.dns.disableIPv6 " from false to True
4- restart firefox

then 

open SYSTEM>Administration>NETWORK
choose your network card
click properties and disable roaming and then select DHCP from the list
click ok and then change to the DNS Tab
now remove the default DNS and put your ISP DNS

i did exactly the above and i have my internet back to normal 
i hope it will for you

---

### Post by autonomouse on 2007-10-21
I had the same problem but it went away when I changed "network.dns.disableIPv6" from false to true, as suggested above. Thanks mshaheen!

Any ideas what was causing it?

---

### Post by c1t1z3n on 2007-10-21
that tweak does enable surfing under firefox... but i still can't get synaptic/apt-get working...

any ideias?

---

### Post by K-a-M-u-Z-u on 2007-10-21
i tried everything **mshaheen** suggested, but still, no internet VIA WIRELESS.
:\
any other ideas? i dont want to install everithing again because i have tweaked all the system...and the tought of doing it all from scratch... :\
i am using XP for a month now. :( and the worst part...i'm getting used to it :mad:

---

### Post by El Rogueo on 2007-10-21
> **K-a-M-u-Z-u said:**
> i tried everything **mshaheen** suggested, but still, no internet VIA WIRELESS.:

Does that mean that your wired internet works now under Ubuntu?

c1t1z3n, that sounds like a configuration problem with apt-get. Can you connect to the internet with other kinds of programs besides Firefox? Your router or ISP may be blocking ports other than 80, or whatever the HTTP one is.

---

### Post by c1t1z3n on 2007-10-21
hm... actually I tried nothing else except FF and apt-get... bud windows works all right (even with online games and p2p etc...) so it shouldm.t be a problem...

( note:  everything worked fine on ubuntu 6.06..    
  7.04 had this problem as well, so i kept 6.06... )

---

### Post by K-a-M-u-Z-u on 2007-10-21
i am not using WIRED connection.only wireless and i have a home network between two computers.
under windows the WIFI internet is working fine and it woked fine in ubuntu 7.04.
i can browse the home network from within ubuntu 7.10.
i can access the router configuration VIA WIFI.

---

### Post by green1152 on 2007-10-21
> **mshaheen said:**
> i have wired internet connection and i had the same problem but it's fixed after doing the following 

1- in firefox type " about:config " in the address bar and hit enter 
2- search for IPV
3- change " network.dns.disableIPv6 " from false to True
4- restart firefox

then 

open SYSTEM>Administration>NETWORK
choose your network card
click properties and disable roaming and then select DHCP from the list
click ok and then change to the DNS Tab
now remove the default DNS and put your ISP DNS

i did exactly the above and i have my internet back to normal 
i hope it will for you

Thank you very much! I too was having issues, but this cleared it up with those simple steps.

Oi. Gutsy was/is a pain to install.

---

### Post by hkullana on 2007-10-26
what is ISP DNS. I am connecting the net through the school lan

---

### Post by El Rogueo on 2007-10-27
> **hkullana said:**
> what is ISP DNS

Internet Service Provider Domain Name Server

---

### Post by paddymi0jpz on 2007-11-03
having same pro guys seemes to be a real problem had to revert to feisty hopefully the problem will be sorted out soon untill then ill leave 7.10

---

