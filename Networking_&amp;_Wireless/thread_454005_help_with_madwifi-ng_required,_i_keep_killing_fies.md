---
title: "help with madwifi-ng required, i keep killing fiesty :("
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by stuck on 2007-05-25
Having had lots of botched attempts at installing madwifi-ng, I come cap in hand and ask for help.

I managed to sort it out in the Edgy, but this time I'm stuck. So far I'm on my third re-install of Ubuntu 7.04 today, thats my eight time this week so far, and still 3 days to go.

```
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci
```

ifconfig ath0 down
ifconfig wifi0 down

These 2 lines close my wireless connection, so how the devil do I >>>>

svn checkout [http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/) madwifi-ng
wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)

Ive tired lots of things, hence the 3 re-installs today.

So far I  am very, very unimpressed with Fiesty, Its begining to look like re-installing edgy, or switching back to Vista that works like a dream.

---

### Post by bradmayne on 2007-05-25
what part of the install are you having trouble with exactly?  I had a hell of a time after upgrading i might be able to help...

---

### Post by stuck on 2007-05-25
Will try runnig through the process again with pen and paper, as I can almost guarentee I will kill Fiesty again, and have to re-install.

---

### Post by stuck on 2007-05-25
```
ifconfig ath0 down
ifconfig wifi0 down
```
at this point i lose my connection

```
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng

svn: PROPFIND request failed on '/trunk'
svn: PROPFIND of '/trunk': Could not resolve hostname `svn.madwifi.org': No address associated with hostname ([http://svn.madwifi.org](http://svn.madwifi.org)
```

Am I missing something, or Is the guide I was following just plain wrong. I think on edgy I downloaded madwifi-ng and the patch then installed them differently.

---

### Post by stuck on 2007-05-25
I tired something else by changing the order of the command so that i got the files first, then did the ifconfig ath0 down etc... but it still failed. Now I cant conect to the net at all, the drivers seem to be gone. And another install of fiesty required. Now I'm in another 24hour period does it stlll count as another install brining my total for the day to 4. Well I might leave it for now and have a sleep.

On a side note, my tota lnumber of install for Microsoft over about the last 15 years is 1. And thats because I recently got Vista. Previous to that never had to re-install windows.

---

### Post by tturrisi on 2007-05-25
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
svn checkout [http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/) madwifi-ng
wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci

0. open a term.

1. download the driver & the patch:
svn checkout [http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/) madwifi-ng
wget [http://patches.aircrack-ng.org/madwifi-ng-r2277.patch](http://patches.aircrack-ng.org/madwifi-ng-r2277.patch)

2. kill the existing driver:
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null

3. use Synaptic to completely uninstall the linux-restricted-modules because it contains the madwifi driver & you will get errors building the new madwifi.

4.  continue in the term:
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
make install
depmod -ae
modprobe ath_pci

or just do the steps when connected via a wire.

---

### Post by stuck on 2007-05-25
Following instruction had to re-install again do to inability to access the net. Probably a simpilar way to fix it than re-install but I'm completely new and cant figure it out.

This is how I got on.

```
0. open a term.

1. download the driver & the patch:
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
wget http://patches.aircrack-ng.org/madwifi-ng-r2277.patch

2. kill the existing driver:
ifconfig ath0 down
ifconfig wifi0 down
rmmod wlan_wep ath_rate_sample ath_rate_onoe ath_pci wlan ath_hal ath_rate_amrr 2>/dev/null
```

No problem.
```
3. use Synaptic to completely uninstall the linux-restricted-modules because it contains the madwifi driver & you will get errors building the new madwifi.

```

I used search on Synaptic to find "restriced modules" it gave me a huge list, but I selected the only one that mentioned madwifi (Atheros)
```
linux-restricted-modules-2.6.20-15-generic
```

```
4. continue in the term:
cd madwifi-ng
patch -Np1 -i ../madwifi-ng-r2277.patch
make
```

At this point its a little fuzzy as Ive had to re-install and could't save any data, but it gave errors something like:
```
/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory

```

> Please be sure you have linux-headers-`uname -r` and build-essential installed, which you can get through Synaptic or apt-get.

So I searched Synaptic to search for linux-headers, it gives me a list of 77 to choose from with 3 already installed.

```
linux-headers-2.6.20-15-generic
linux-headers-2.6.20-15
linux-headers-generic
```

Before I try something else and kill Fiesty again, a little more assistance would be really helpful.
Sorry for what must seem like simple stuff to you.

---

### Post by tturrisi on 2007-05-25
apt-get install build-essential
and just to be sure:
apt-get install linux-headers-`uname -r`
(not the use of reverse apostrophes)
then: rebuild the driver

---

### Post by stuck on 2007-05-25
Not sure why, but it kept failing to work.

So I had to reboot and try again about 3 times from the begining. (But no Fiesty re-install required)

I didnt know any better so tried from step1 each time, sometimes it gave errors about things being done allready, but I ignored them and carried on.

Wow, really cant believe how much youve helped me. Youve managed to help me get sorted in a few "easy" steps. Even following numerous guides I was getting nowwhere fast.

Ive looked though some of your posts and see that you appear to be using aircrack-ng.

I have been using aircrack-ptw to greater/faster effect. I hope this link proves as valuable to you, as you have been to me. Dont know how else to thank you.

[[COLOR="Red"]Aircrack-ptw[/COLOR]]("http://wirelessdefence.org/Contents/Aircrack-ptw.htm")



Mark.

---

### Post by tturrisi on 2007-05-26
Thanks, I'll give -ptw a try.
I dual boot xp-etch.  last night I got aircrack-ng to work in windows xp using peek atheros driver that supports monitor mode!  No native injection, gathering ivs takes a while, but it works well and faster if there are many clients associated with the wlan.

---

### Post by stuck on 2007-05-26
I'm Quad booting.

BT2 --- I find it really good, been using it for a while. Everything worked straight away for me. Try the live CD.

[[COLOR="Red"]BT2[/COLOR]]("http://www.remote-exploit.org/backtrack.html")

Vista, XP and Ubuntu.

Having major problems getting desktop effects working, So Ive only given Ubuntu 7G space to try and move over from MS.

Give the BT2 thing a try, pretty sure you will like it.

---

### Post by tturrisi on 2007-05-26
Oh yeah, I already have BackTrack2, it's pretty slick.
And thanks again for the link to aircrack-ptw, I cracked my own 64 bit key in less than 40k packets, took all of 1.5 minutes!

---

### Post by ischnura on 2007-06-21
Hi Tturrisi,

Just just want to thank you for helping us. I got stuck with the same problem as Stuck and I got it working by following your guidance!

Thanks again,

Juan

---

