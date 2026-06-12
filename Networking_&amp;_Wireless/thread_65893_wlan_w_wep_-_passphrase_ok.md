---
title: "wlan w/ wep - passphrase ok?"
date: 2005-09-15
forum: Networking &amp; Wireless
---

### Post by Florian Hufsky on 2005-09-15
I use an wlan accesspoint with wep encription and a passphrase.

however i can't get a dhcp adress, so i guess I'm using the wrong password (because when switching off encription and setting no password in ubuntu everything works fine).

is there a way to tell if my password was correct, so i can find out if the problem is somewhere else?

and if yes - why on earth doesn't the network manager in gnome report this to me?

i can give ifconfig/iwconfig output if needed for this.


i've been going through an endless amount tutorials and forum threads on dhcp + wep / wlan issues and hope you can help me.
some said you have to add s: in the passphrase field to use asci passphrases, but i have upgraded to breezy which includes an option to set asci anyway.

what bothers me though, is that man iwconfig says that wep passphrases are not support. but i was able to connect to a wep passphrased router at school for 10 minutes. then it somehow disconnected me and now i can't. at home (also wep + passphrase) i was never able to connect though.

please help me, i'm desperate as hell.
i'm going to add everything i learn here to the ubuntu wlan wiki anyway.

---

### Post by mlomker on 2005-09-15
Are you trying to set things in the /etc/network/interfaces file or using a graphical program?  Maybe you could post the contents of that file.

Have you looked at a program called wpa_supplicant?  It's command-line but works well.

Have you looked at the GTK Wifi application (there's a forum for it on here)?  It looks cool, but I run KDE and do things from the command-line instead.

---

### Post by Florian Hufsky on 2005-09-15
first: thanks for answering!

i use the graphical programm that comes with gnome, i can still post the content of my /etc/network/interfaces if you like.

Hower I seem to have found a "solution" (or merely found out a bit more):

128bit ASCI - doesn't work (yes, the strings are prepended with s: in /etc/network/interfaces)
128bit HEX - doesn't work
64bit ASCI - doesn't work
64bit HEX - does work (yay!)

this is kind of weird.
however the not working 128bit keys go with man iwconfig, which says that passphrases are not supported.
i'm not very into wep stuff, but alas i guess 128bit keys are called passphrases, wheres 64bit keys are ... well... just... simple plain, ubuntu supported, wep keys

the only thing that bugs me is that ASCI won't work, but i can live with that (for now).

if this is a bug it should be documented somewhere.
and if 128bit wep keys don't work it should be documented somewhere too.
btw, i use ipw2200 v 1.0.6 (basically the current thing you get out of breezy) and no wpa_supplicant yet (maybe wpa_supplicant supports bigger wep keys and the like? (i think i heard that wpa_supplicant has a wep capabilitie too)

however the error messages in ubuntu are quite misguiding (as there are none for wlan dhcp timeouts in the graphical interface).


uhmm... yes... after all this chatter i still have a question:


is ubuntu capable of 128bit WEP encryption?
is ubuntu capable of 64bit WEP, enterred as ASCI string, or am i too stupid to get this right?

---

### Post by mlomker on 2005-09-16
To be honest, you know more about this right now than I do.  I don't use encryption at home, just MAC security.  I figure if someone knows how to spoof a MAC then they probably have airsnort for cracking the key as well.  :grin:  My AP doesn't support the fancier encryption types.

The only thing that comes to mind is that the GUI you are using might not support as many modes as wpa_supplicant can.  I have the same wlan driver, ipw2200 and it is fully supported.  You might want to [take a look](http://hostap.epitest.fi/wpa_supplicant/) at some of the docs out there.  It's a good tool...basically it is a daemon that 'watches' for an access point listed in its configuration file and automatically attaches you to it with the proper keys/settings/etc.  It takes some time to deal with all those text configuration files but once you're done you don't have to do anything...once in range it just works--just like Windows! (ducking and hiding).

---

### Post by Florian Hufsky on 2005-09-16
ok, thanks.

---

### Post by Florian Hufsky on 2005-09-18
I've added the stuff i learned to the wiki: [https://wiki.ubuntu.com/WLANHowto](https://wiki.ubuntu.com/WLANHowto)

---

### Post by ricesteam on 2005-09-19
Any luck with solving the problem?

I'm having the same issues with WEP...seems a little buggy.

My wireless only works without encryption, which is unsafe to me.

---

### Post by Florian Hufsky on 2005-09-20
I solved it by switching to 64bit WEP.

concerning 128bit i guess the following:
i don't know how 128bit wep works, but i guess it takes the passphrase and generates a new encryption thingy for the whole network every 15 minutes or so.
however ubuntu only manages to get one of these encryption thingies right, so you will only get the right connection thingy each x-ed time, when the generated one is the same as ubuntu creates.

what brings me to this conclusion is that wep 128bit worked fine for ~15 minutes, then 45 not at all and then 15 minutes fine again.

but this really doesn't help very much.

however: i think i read somewhere that wpa_supplicant also supports wep, so i might give it a try.

---

### Post by ricesteam on 2005-09-20
I can't seem to get 64 bit working either.  I wonder if it is hardware related.  I'm using Linksys WPC54G card, and my router is a D-Link DI-624.  But I doubt it because the two works perfectly fine in Win XP.

I'm positive my key is correct because I made it simple in the testing...ie. BABABABABA.

Even with s: prefixed, I cannot establish a wireless connection with WEP enabled.

---

### Post by mlomker on 2005-09-20
> I'm positive my key is correct because I made it simple in the testing...ie. BABABABABA.


I don't use WEP, but I'm curious.  What driver does that card use--Atheros or ndiswrapper?  Are you putting in the key in /etc/network/interfaces, with iwconfig, or with wpa_supplicant?

---

### Post by Florian Hufsky on 2005-09-20
[QUOTE=ricesteam]I can't seem to get 64 bit working either.  I wonder if it is hardware related.  I'm using Linksys WPC54G card, and my router is a D-Link DI-624.  But I doubt it because the two works perfectly fine in Win XP.

I'm positive my key is correct because I made it simple in the testing...ie. BABABABABA.

Even with s: prefixed, I cannot establish a wireless connection with WEP enabled.[/QUOTE]

try setting your d-link router to work with no key at all ans see if that works, then you know wether it's a key or driver problem.

---

### Post by steve0921 on 2005-09-20
I also seem to be having this same problem with 128bit WEP (hex). I have tried almost everything (built-in drivers, ndiswrapper, interfaces file, wireless-tools, several network GUIs) except haven't finished installing wpa_supplicant yet. I can also connect to the unencrypted network nearby.

I was wondering:
1. If anyone has found a solution other than just switching encryption methods (an inconvenience for other people using this network).
2. Is there a specific format needed to specify hex keys? (dashes separating groups of four, caps/lowercase for abcdef characters) Could this make an otherwise correct password seem wrong?

Thanks in advance.

---

### Post by mlomker on 2005-09-20
> 2. Is there a specific format needed to specify hex keys? (dashes separating groups of four, caps/lowercase for abcdef characters) Could this make an otherwise correct password seem wrong?

There are a number of [threads](http://ubuntuforums.org/archive/index.php/t-282.html)  about this.  I don't use WEP, myself, otherwise I'd give more specific advice.

---

### Post by ricesteam on 2005-09-20
@Floriam Husky - Works without WEP encryption.  But i need some sort of encription going on because I feel a little paranoid having my line open.

@mlomker - I am using ndiswrapper, the latest version according to Synaptic Packager.  I've tried putting in the key via iwconfig, the gnome-gui network setting, and manually editing /etc/network/interfaces.  

I haven't tried WPA-Supplicant; I don't know if my card supports it and I don't know if it is stable on my DI-624 router.

I am also wondering if Linux/Ubuntu is translating the HEX key into something unrecognizable by the router...

The only protection I have is MAC filters (to prefent ouside access)...but people can still listen into my connection.

Another thing I notice is I have to broadcast my ESSID so my card can pick it up or else it won't work. Encryption or not.

---

### Post by Florian Hufsky on 2005-09-20
ok, if it works without encryption the encryption should be the problem.

first try 64bit WEP and enterring the key as hex. this should work fine (at least i got it to work without problems).

---

### Post by mlomker on 2005-09-20
> I haven't tried WPA-Supplicant; I don't know if my card supports it and I don't know if it is stable on my DI-624 router.


It supports ndiswrapper.

> 
I am also wondering if Linux/Ubuntu is translating the HEX key into something unrecognizable by the router...


You'll find quite a few threads about this, especially discussing 128-bit keys.  It seems that they have to be inputed as ASCII and not hex.  You preface the ASCII with **s:** on the line.

> 
The only protection I have is MAC filters (to prefent ouside access)...but people can still listen into my connection.


That's what I use too.  I figure if someone can spoof a MAC address then they'll know how to use airsnort to crack encryption as well....so why bother?

> 
Another thing I notice is I have to broadcast my ESSID so my card can pick it up or else it won't work. Encryption or not.

I've seen some threads about that too, but I just leave mine on.  Have you tried registering by the MAC address instead of the name?  Look at **man iwconfig** and you'll see an entry for the **ap** option...looks interesting.

---

### Post by Ainvar on 2005-09-20
The funny thing about this I am having the same issue with 128bit keys and even using ascii input I am having this issue. It started about 4 days ago after a Breezy update.

I have gone as far as manually redoing my ipw2200 drivers and the ieee80211 along with the ipw2200 firmware. I have also gone as far as reinstalling all the base kenel packages and not updating Breezy after the preview install from cd and it works perfectly every single time.


I am at a lose as to what is causing this error.


Sorry I know this is a thread in hoary but I have found this to be the issue only in the latest install of breezy for me.

My hardware is Dell Inspiron i6000D with the intel 2200 b/g card

---

### Post by mlomker on 2005-09-21
> Sorry I know this is a thread in hoary but I have found this to be the issue only in the latest install of breezy for me.


Have you been watching the breezy forums?  I've read other threads there regarding this and I believe it is known to be broken.

I tried breezy for two days but I had a couple key things that I couldn't get to work.  I'm going to wait for release, myself.  There's nothing that breezy offers for me that hoary didn't.

---

### Post by knubbe on 2005-09-21
I had the same problem until yesterday (20th of September) when i ran "apt-get upgrade" again. 

Now it works. WEP with 64 bits key and i use all settings from the GUI instead of the commandline. 

I have a dell inspiron 6000, Intel ProWireless 2200 and i run Kubuntu Breezy 5.10 (preview, with "apt-get dist-upgrade" and "apt-get upgrade" done).

The default installation of Kubuntu 5.10 preview was VERY unstable (kde crashed alot and there were problems to get the ethernet working, the wlan worked though - even though it didnt work with WEP) for me so i really recommend to keep the system up to date.

That was my five cents..

---

### Post by Florian Hufsky on 2005-09-21
thanks - i'll try upgrading.

---

### Post by Ainvar on 2005-09-21
Thanks all for the update. I will make me a second wep key on the ap to do 64bit for linux to use for now.


Ok, Here is something you all might find interesting. I went through and deleted the interfaces file in the /etc/networks folder and then I also deleted the profile.xml file located in /etc/gnome-system-tools/network.profiles.xml and then reconfigured my wifi card and it worked with 128bit wep key and I can do either static or dhcp (ieven made a profile for both). I then configured my broadcom nic card on my laptop and made two profiles for that dhcp and static. After all this I rebooted and then switched from one profile to another after I logged in and it worked!!!!

I will take my lappy to work tomorrow and setup my 2 profiles for that and check out wifi and lan there to see if wifi breaks there or at the house tomorrow.

---

