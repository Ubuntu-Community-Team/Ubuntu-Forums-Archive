---
title: "ndiswrapper killed all my nics"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by velozoom on 2006-11-06
As  noob to linux, I am lost.....I installed ndiswrapper and used it to install the bcmwl.5inf driver for my broadcom wireless card on my HP dv9000 laptop.  

It did not work and ndiswrapper said the hardware was not present.  I uninstalled the driver and tried again, blah blah blah.  

Now, all my nics are dead.  iwconfig shows "no wireless extensions" for all my nics save for the wireless which isn't working anyway.  eth0, which is the wired nic, is unrepsonsive and will not get an ip although link and activity lights on the port are on and active.  

How did this set all my nics look for wireless extensions and how can I at least get wired lan capabilities back?

---

### Post by velozoom on 2006-11-06
Bump.....

Really need some help on this one, I have to get a couple files off my laptop and with all the nics being offline........  (I don't even know if the cd burner works, not tried it yet )

---

### Post by sekim27n2 on 2006-11-07
Is it possible that you nic hasn't obtained address information.  As root you could try to run

#dhclient

It will automatically attempt to get an IP address for your cards.  If that doesn't work, I might suggest making sure that your /etc/modprobe.d/ndiswrapper is removed and try rebooting.  Hopefully one of these two options will help you out.

---

### Post by ckonrad on 2006-11-07
my personal opinion is that the best thing to do if you want to use wireless with linux is to buy a wireless card that works out of the box with linux then you dont have to futs around with ndiswrapper and you will also be supporting companies that get the whole open source philosophy. 

if you want to or have to use ndiswrapper, go ahead and uninstall ndiswrapper from your system, and then uninstall that driver you have on there now and go ahead and download this little package from here [http://compwiz18.blackhole.cx/bcm4318/get.php?file=bcm4318.all.tar.gz](http://compwiz18.blackhole.cx/bcm4318/get.php?file=bcm4318.all.tar.gz)

that package has ndiswrapper and your driver and a nice little shell scipt that does most of the configs for you. All you have to do to install that is to cd to the directory you downloaded it from and then unzip it, then cd o that unzipped directory and then type this to run the script

sudo ./ndiswrapper_setup

your light should pop on a few seconds later if it doesnt then press your wireless button.

then go to your network settings manager under administration and choose your wireless interface and go to properties and configure it, choose your ESSID that you want it to connect to put in a key if you have one for the wireless network etc. The network settings manager in gnome doesnt seem to have some important settings listed in the gui, so you will need to open up your interfaces config file and do it manually which is really the easiest way to do it anways. After you have activated and configured your interface in that network settings manager, open up a terminal and type this.

sudo gedit /etc/network/interfaces

add these 2 lines

wireless_mode managed
wireless_keymode open

then restart your system and everything should work fine. I have used that method many times with laptops with broadcom but that method doesnt seem to work with the new edgy eft version.

---

### Post by dmizer on 2006-11-07
> **velozoom said:**
> eth0, which is the wired nic, is unrepsonsive and will not get an ip although link and activity lights on the port are on and active.  

How did this set all my nics look for wireless extensions and how can I at least get wired lan capabilities back?

if the link and activity lights are on and active your wired nic probably is working fine.

1) edit interfaces:
```
gksudo gedit /etc/networking/interfaces
```
remove the section about wlan0, save and exit gedit

2) restart your network:
```
sudo /etc/init.d/networking restart
```

3) see if you have an ip on your wired card:
```
ifconfig
```

ifconfig for wired network cards
iwconfig for wireless

---

### Post by velozoom on 2006-11-08
thanks all, I got wired back but one oddity (I think) is that the /etc/networking/interfaces file appears to be non-existant.  gedit couldn't find it and nano created a new file.  Not sure what that means.....

And a stupid noob question-- where do I see what drivers are installed and how do I remove them?  how do I uninstall ndiswrapper and try the package dmizer suggested?  

thanks again for the help!  :)

---

### Post by dmizer on 2006-11-08
"man" is your best friend.

man ndiswrapper ;)

to list the drivers installed,
```
ndiswrapper -l
```
after you've listed your drivers, then you know what ndiswrapper is calling them.  you can remove them with this command:
```
sudo ndiswrapper -e driver
```

btw, i did not suggest any wireless package.  your question was how to disable ndiswrapper so you can get access via wired lan.

if you still want to make your wireless adapter work, we'll need to know what ubuntu calls it, so with your wireless adapter connected, please post the output of:
```
lspci
```

ps. i have been reading that the directory structure for edgy is quite different than in dapper (which is maybe why you don't see /etc/networking/interfaces), so i may have to restrain myself from answering edgy questions ... :(

---

### Post by velozoom on 2006-11-09
sorry, dmizer, I meant the package ckonrad posted a link too.  

ckonrad, I tried to run ndiswrapper_setup but it won't install on a 64b kernel, just FYI.....  :)  

This is odd, my wired NIC still won't automatically grab an ip but I have to use dhclient to force it.  

I appreciate all the suggestions, I have a couple things I am goint to try when I get home from work tonight and if they dont' work I'll be back....  ;)

---

### Post by dmizer on 2006-11-10
ahh ... there's the key: you're running the 64b kernel!

i would suggest you go with the i386 kernel instead of the 64b kernel.  the 64b install is always in constant need of baby sitting, and configuration is iffy.  you've bitten off a pretty big hunk of linux to install the 64b kerel from the outset.

the i386 kernel will work with a much broader variety of software, and will be a much easier transition for you into the linux world.  for daily use, you'll not notice a performance difference.

---

### Post by velozoom on 2006-11-12
>>i would suggest you go with the i386 kernel instead of the 64b kernel.

I've actually been thinking the same thing as much of my reading has said almost precisely the same thing- 64 is still a bit twitchy.  

This question may be drifting the thread a bit off topic for this discussion group, but I'll ask anyway.  ;)  

Is it possible to install the 32b kernel without completely uninstalling Ubuntu and having to start all over?  If it's possible, is it recommended?  I know that I would never do a comparable thing (upgrade from Win2K to XP for example) on Windoze but would always to a wipe and clean install.  The impression I've gotten is that the kernel is far less integrated in Linux than it is in Windows and can be modified and changed without crashing the whole system.  Again, sorry for the basic Qs but I'm still trying to sort out the overall paradigm and structure of Linux.....

Thanks for all the help!  :)

[EDIT] actually, after thinking on it for a moment, I realize I will probably be better off doing a complete reinstall.  I have all the 64b driver installed for my vid card and wired nic.......but will a 32b kernel install on an AMD64 hardware platform?

---

### Post by dmizer on 2006-11-14
yes ... the 32bit kernel will install on a 64bit platform with no problem.

you can save your home directory if you move it to a separate partition (this will save your theme, desktop settings, and other user specific options), but as you've already noted yourself; if you've installed any 64 bit specific hardware drivers or other software, you're probably better off with a clean install.

remember to upgrade to the 686 kernel after the install.  your system will be more stable and responsive.

btw, i think the peloton would leave you out of the draft for saying that windows 64bit is more "integrated".  remember, windows wrote NONE of it's own drivers.  windows puts out the os only. hardware manufactures are expected to take up the slack.

---

### Post by velozoom on 2006-11-14
>>btw, i think the peloton would leave you out of the draft for saying that windows 64bit is more "integrated".

Lol, I meant the kernel, not the drivers.  Besides, most of the guys in my peloton barely know how to dial a cell phone.  This conversation would give them headaches in about a minute....  

I installed the 32b already but then could not get the vid drivers working.  the i386 drivers did not work and my video is FUBAR again.  Ugh.  

I am wondering if I should revert to dapper as edgy seems to be too much, too soon to sort out for me at this time.  Sadly, I have to go to work now and get my head back into the Windows way of doing things......

---

### Post by dmizer on 2006-11-14
windows was and still is behind linux for their 64bit kernel.  remember, you're having problems with peripherals not the kernel ;) you might find this to be a very interesting read: [wikipedia link]("http://en.wikipedia.org/wiki/X86-64")

what video card do you have?

care to share your other gear?
trek 2300 frame built up myself with a kestrel ems pro fork and bars, easton ec70 post, and i love my mavic ksyriums, i run dura-ace on the back and ultegra for everything else except my FSA cranks and king headset.  rock solid in the final 100 ;)

too bad life's gotten the best of me this last year.  i'm so out of shape it's not funny.  maybe it's time for me to start thinking about liggett's throne ... lol

---

### Post by velozoom on 2006-11-14
got the vid card working, I forgot I had to disable the "nv" driver in the disabled modules list.  once I did that it worked swimmingly.  And I went back the 64b kernel, LOL, I decided I am too stubborn and I like a challenge.  

Things have gone a lot better this time around and I've made far less of a mess of things.  

I installed ndiswrapper this time and discovered a mistake I didn't know I made- I only had the .inf file for the driver on my previous installatin, I didn't have the .cab or .sys files!  ndiswrapper never gave me a warning about that on the first go, however, it just said that the driver was installed but the hardware was not present.  Odd, that.  Now it shows both the driver being installed and the hardware being present (progress!!) BUT I still have no WLAN.  The SSID and key are config'd correctly.  When I run #dhclient eth1 I receive the following error:
```

# dhclient eth1
SIOCSIFFLAGS: No such file or directory.  
SIOCSIFFLAGS: No such file or directory.  

```

I get the error twice as shown above.  I've read that this error is from the system not being able to find the firmware for the wnic but I've not found a solution....I am assuming I would just have to move the files to the proper place and recompile them with ndiswrapper but I don't know where that would be.....who said ignorance is bliss?!?!?!

[EDIT]....also the wireless is not appearing in network tools.....and how the bloody heck am I supposed to choose between WEP, WPA, or WPA2?  There seems no option for that!  Argh!  



Now for the really cool and fun stuff- 

I just ordered a custom [STRONG]("http://www.strongframes.com") frame with Columbus Muscle seatstays from Carl Strong from Montana, USA.  It just got out of the paint shop and will be in my greasy little hands by December......

I'm going to Record 10 from DA 10 for this bike....for no real reason other than I love the CF levers and components of the Campy drivetrain.  Columbus Muscle fork, FSA team issue cranks, 54/42 rings, Easton EC90 bars, FSA carbon stem, Chris King HS.  Everything will be black/white as much as possible although the FSA stuff has too much red on it.  ;)  

Here is a pic of my previous roadie that I crashed out a while ago necessitating the replacement frame.  This pic is about 3 years old, I've upgraded most components since then, especially that fugly bar tape!!!!  I loved this bike but the builder isn't making frames any longer so I could not replace it with another.....

 
[img]http://www.cginy.net/Anvil1.jpg[/img]

Hoping to get back into racing next season.  Need to start training NOW.  I've not raced in three years- single parent, full time job, side biz doing web development....no time for +25hour/wk training schedules!  Kids are older now, I am pretty ticked off at being 20lbs overweight, and I am motivated.  07 could be a good year.  ;)  

Yer a sprinter, eh?  (final 100....) I can't spring to save my life.  I am a break away artist/time trialist.  The last crit I was in was in '03.  I was in perfect position in the last corner, 4th through the turn, and ended up finishing 32nd!!!   LOL!!  I really *can not* sprint!  

How's the racing scene in Japan? 

Rob, Category 2 road racer, NY, USA.

---

### Post by dmizer on 2006-11-14
well, you've gone back to the relm in which i really can't offer much support other than moral ... lol.  might take a look at dmesg.  also, usually ndiswrapper labels wnic's as wlan# rather than eth#

i LOVE bell laps, and my favorite color is GREEN! :mrgreen:  scene is not much different than the states.  lots of elbow bumping, threshold crits and short (nothing longer than 100km or so) road races.  

actually, it's too bad there's nothing stateside to really showcase your talents (at least not when i was looking at the circuit a couple years back).  i always craved longer stuff, but i could never find it.

sweet ride there, but i hated how noisy the zips are ... impossible to sneak up on anyone.  but i'm still jealous, wish i had the dough to plunk down on a custom strong.  i love steel too.  still have and ride my [steelie ]("http://www.celoeuropa.net/accessories/image_specials/schwinn_circuit.jpg") from back in my juniors racing days.  would also love to wrap my legs around some ti ... mmmmm.

---

### Post by velozoom on 2006-11-14
Dmesg tells me that something can't find something....lol, is that technical enough for you?  
```

[  347.818852] IPv6 over IPv4 tunneling driver
[  365.366948] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  365.381052] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4773.315421] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4773.322505] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5753.721323] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5753.735736] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6335.273311] eth0: link up.
[ 6335.274295] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6339.410319] eth0: no IPv6 routers present
[ 6340.009462] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6340.016628] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 9133.614593] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 9133.629392] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 9922.387137] wireshark uses obsolete (PF_INET,SOCK_PACKET)
[10778.563367] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[10778.578249] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


```

I guess the question I have now is- do I need to compile the driver/firmware from or to a specific location?  Also curious about the notations on the IPv6 stuff.....do I need to somehow disable that or install an IPv6 protocol component to the networking?  

The Strong was *quite* reasonable, especially when you consider what Ti and CF are going for these days.  I paid $1650US (delivered) for the frame, which included a $300 upcharge for the carbon seatstays and a single color paint job (love the black) with my name on the top tube.  Carl is easy to work with and really wants the customer to be happy.  A basic steel frame would only run you $1200US plus delivery.  Not sure what shipping or import tariffs would be to Japan but I can't imagine it would be as much as a carbon seatstay!!  ;)  

Here's my other custom-

[img]http://www.cginy.net/AnvilTT.jpg[/img]

---

### Post by dmizer on 2006-11-14
lol!

black list that puppy.

```
gksudo gedit /etc/modprobe.d/blacklist
```
and add "blacklist bcm43xx" to the end of the file.  before you save, make sure there is a blank line -> <enter> AFTER your new line.

too bad he doesn't make those frames anymore huh?  matching set and all.  personally, i don't even own a tt setup.  lol ... the sprinter in me doesn't agree with that gig.

---

### Post by velozoom on 2006-11-14
Blacklisted. 

No effect.  ](*,)   ;) 

Yeah, the matching set thing sucks.  Mais c'est la vie, non?  

I am going to save up and get some stupid aero carbon thingy in a couple seasons.  I'll wait and see what the coolest thing is when I can afford it.  Right now the top spot on my drool list is a Cervelo P3 carbon.......gggggrrggrgrhgrgrhghgrhgrrhrgr.....ca-a-a-a-a-a-a-a-a-ar-bon

Think I am going to try this over on the 64b forum.....might be a 64b issue that someone has run across.....

---

### Post by prince_niceguy on 2006-11-15
Check this thread out. If it is bcm4318 it should work. 

[http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

Has worked for me. Make sure your driver is 64 bit. If you are using the driver taken from your laptop it might be a 32 bit driver. If your windows versions is XP professional then it is 32 bit. If it is XP professional 64 bit (which I doubt as no laptop manfacturer give XP professional 64 bit), then it is 64 bit.

---

### Post by velozoom on 2006-11-15
the driver is 64bit as downloaded from nvidia.com  HP is too *&% cheap to ship actual disks anymore.  Morons are using a partition of the HDD as a recovery area.  So what happens in case of HDD failure?!?!?! 

I've seen that thread but the card is a BCM4310 UART  Thank, though.  :)

---

### Post by dmizer on 2006-11-15
okay ... take a look at dmesg again, see if you can find your adapter listed as wlan this time instead of eth

also, just because the howto is not written for your card specifically does not mean that you can't use information from it.  though it looks like we've already done pretty much everything the howto suggests anyway.

i've loved cervelo since they first came out (back before they were using carbon).  i even had their first p2 tt bike (bright orange) as my wallpaper right after i saw wohlberg astride the thing in the 96 olympics. HOT.  use to frequently visit my local shop where they had one frame hanging up on a wall ... just out of reach, right next to the all carbon kestrel my my.

---

### Post by velozoom on 2006-11-15
I've been all through those steps a dozen times.....*sigh*

Ok, I am really surrendering this time, stubborness or no stubbornness.  There are a bunch of guys on these forums who tried and tried and ended up with the same result- some broadcom nics just won't run on Edgy 64.  Now that every bloody thing else is working on the box, it looks like it's time to run the 32 bit version.  It's funny that the 32b has different installation screens than the 64b.  Going to archive all my drivers and gnome themes and send it off to my winblows box for short stay there while I wipe and reinstall.....*sigh*

Cervelo is the shiznit and if I had $3k to burn......ooooooooo baby.....

[img]http://images.competitivecyclist.com/images/products/cervelo/2006/p3c_zoom_1.jpg[/img]

---

### Post by dmizer on 2006-11-16
> **velozoom said:**
> I've been all through those steps a dozen times.....*sigh*

Ok, I am really surrendering this time, stubborness or no stubbornness.  There are a bunch of guys on these forums who tried and tried and ended up with the same result- some broadcom nics just won't run on Edgy 64.

lol ... i would've just plunked down a few bucks for an adapter i knew would work in the 64bit ;) ... you have two bikes for the same reason ... no?  one bike for the road races, and one for tt.  why not two adapters.  one for the windows machines, and one with drivers which cooperate in the 64bit linux.

---

### Post by velozoom on 2006-11-16
lol, because I just spent over $1k on this bloody laptop with an integrated wireless nic and bluetooth.  There is no way in heck I am buying an addon.  I'll beat this thing into submission, yet.  

Installed 32b.  Everything is back to where it was before.  ndiswrapper installed the driver, shows driver installed and hardware present, but eth1 (system still shows it as eth1) is not appearing in network tools.  Going to go back over all the stuff earlier in the thread later.....

Cheers

---

