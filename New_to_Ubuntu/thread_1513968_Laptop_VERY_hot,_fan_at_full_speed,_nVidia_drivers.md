---
title: "Laptop VERY hot, fan at full speed, nVidia drivers worsen resolution"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by crowhill on 2010-06-20
hi there

it seems i have some severe hardware problems. my dell xps m1330 laptop is getting very hot. ever since i run ubuntu on it i noticed this issue. however, after i did a fresh reinstall the other day things have gotten worse.

it seems (according to 'top') my cpu usage is fine. xorg spikes up every once in a while and firefox requires the usual resources but otherwise it looks ok. however, the touchpad feel incredibly hot and my fan won't stop spinning.

i'm pretty sure this has something to do with my graphics card. i have this nvidia card and the drivers offered in 'synaptic' make my screen resolution worse and not better.

at the moment, the nvidia driver is not installed and i'm not intending to install it. however, i'd like to get the heat and the fan spinning under control.

ever since i installed ubuntu on this laptop i got this problem. in fact, i had to send the laptop to dell support twice and each time they told me that the motherboard is fried and needs to be replaced. i don't want this to happen again.

how can i stop my fan from spinning so much? how do i even monitor its spinning?

thanks so much! i really can't stand windows anymore but if ubuntu keeps frying my hardware, something is going wrong.

cheers,
crowhill.

---

### Post by yossell on 2010-06-20
I have the m1330 laptop too. You don't confirm whether you've got the Nvidia chip or onboard graphics but I assume, since you're talking about the nvidia drivers, it is the nvidia chip. Apart from the third paragraph below, none of the following will apply if you have the M1330 with onboard graphics.

When I first installed Ubuntu on my computer, it ran much hotter too. But my current set up runs cooler than windows, and I can squeeze out more battery life as well - I can't definitively say what made it better, but I can tell you what I did to make things work better. 

Firstly, overheating is a BIG problem with this laptop whatever the operating system. There's a known problem with the nvidia 8400 chip, but Dell's dreadful thermal pad makes matters worse. As a partial fix, Dell's latest bios have an aggressive fan setting and I would not recommend overriding the fans' settings: they need to work hard to keep the components of this computer cool.

Secondly, I *have* installed the non open source nvidia drivers - I think they do a better job of power management and keep the graphics chip cooler than it is otherwise. My screen resolution is fine, they work great, I can enable desktop effects, do the cube etc. etc.. If you have the same graphics chip, there surely should be a way of getting them to work on your machine, as they work on mine. I can share my config files if you want to give it another go. I'm no expert, so I don't know what does what - but you may find it helpful. 

Thirdly, I use the program powertop - I run it as root and follow its suggestions. In particular, I think that Ubuntu tends to run an aggressive cpu policy, running the chip fast and so hot. Alternatively, adding cpu frequency scaling monitor to gnome-panel and setting it to 800mhz or powersave, runs chip slower and cooler. 

Finally, I have removed the appalling thermal pad and replaced it with a copper shim, so that thermal conduction between graphics chip and heatsink is much better - and this makes a massive difference. It's not as hard as it sounds, and I highly recommend it if you want to reduce your chances of facing the problems of the doomed nightmare 8400 chip.

[http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html](http://forum.notebookreview.com/dell-xps-studio-xps/268081-dell-xps-m1330-nvidia-geforce-8400m-gs-copper-mod.html)

is a great step by step how to.

---

### Post by The Real Dave on 2010-06-20
With any laptop, dust can be a serious issue. It's easily picked up if you leave your laptop on a bed, carpet or chair, and it clogs the systems terribly. 

Buy yourself a can of compressed air, open up your laptop (if your comfortable with that), and try to spray away any dust. Using a vacuum cleaner at the same time is a good idea, so that the dust doesn't just fall back down, but be careful of static.

One place in particular to watch out for are the heatsinks. These clog up easily, and it's essential they're kept clean, otherwise they just don't perform as they should. It also puts extra stress on your fans, making them run harder and faster than they need to. If possible, remove your heatsink and clean it well. Remember though, that if you break it's contact with the CPU or other chips, you'll need to clean off the old thermal grease/pad and apply new grease. Artic Silve 5 is brilliant stuff.

If your not comfortable opening up your laptop (those things are often like a ship in a bottle), take your laptop to a computer repair shop, and get them to clean it out.

---

### Post by warfacegod on 2010-06-20
> **The Real Dave said:**
> With any laptop, dust can be a serious issue. It's easily picked up if you leave your laptop on a bed, carpet or chair, and it clogs the systems terribly. 

Buy yourself a can of compressed air, open up your laptop (if your comfortable with that), and try to spray away any dust. Using a vacuum cleaner at the same time is a good idea, so that the dust doesn't just fall back down, but be careful of static.

One place in particular to watch out for are the heatsinks. These clog up easily, and it's essential they're kept clean, otherwise they just don't perform as they should. It also puts extra stress on your fans, making them run harder and faster than they need to. If possible, remove your heatsink and clean it well. Remember though, that if you break it's contact with the CPU or other chips, you'll need to clean off the old thermal grease/pad and apply new grease. Artic Silve 5 is brilliant stuff.

If your not comfortable opening up your laptop (those things are often like a ship in a bottle), take your laptop to a computer repair shop, and get them to clean it out.

+1 to cleaning. If your heatsink (hunk of metal screwed over the CPU) has radiator fins (it should), be certain to get the dust between the fins.

---

### Post by crowhill on 2010-06-20
> When I first installed Ubuntu on my computer, it ran much hotter too. But my current set up runs cooler than windows, and I can squeeze out more battery life as well - I can't definitively say what made it better, but I can tell you what I did to make things work better. 

first of all, i've got

> VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

i haven't installed the driver from the system -> administration -> hardware drivers yet and this is good so as this driver makes my screen resolution worse.

can you tell me more details about what you did? which drivers did you install and how did you get them?

thanks so much for you help,
i really appreciate it!

cheers,
crowhill.

---

### Post by poldie on 2010-06-20
> **warfacegod said:**
> +1 to cleaning. If your heatsink (hunk of metal screwed over the CPU) has radiator fins (it should), be certain to get the dust between the fins.

In my experience, regardless of OS, ALL laptops run too hot ALL the time, and you need to underclock them, disable graphics settings to degrade performance etc or they'll just freeze/reboot from time to time.  Perhaps there's another diagnosis/solution, but this has always worked for me.   

Only expensive, higher-end laptops seem to be safe from this problem, and on those you can tell when they're getting hot because the fan suddenly becomes audible and you feel the hot air coming out.

---

### Post by crowhill on 2010-06-20
dust is most likely not a problem in my case as i got it cleaned only a few months ago.

under windows, my laptop does NOT become as hot! this must be a linux/ubuntu thingee.

---

### Post by yossell on 2010-06-20
@crowhill

(edit: ignore this bracket - i was writing while you posted: Incidentally - the others are right! A good cleaning of any dust that may have accumulated is always a good start - have you tried powertop?) 

I have the nvidia accelerated graphics (current version) on my system and active.

Like yours, the chip is a GeForce 8400M GS - but I don't know the revision number and I don't know if it makes a difference. The screen is running at 1280x800 which I believe is its native resolution. 

You say when you install this driver the resolution is wrong?

---

### Post by warfacegod on 2010-06-20
> **poldie said:**
> In my experience, regardless of OS, ALL laptops run too hot ALL the time, and you need to underclock them, disable graphics settings to degrade performance etc or they'll just freeze/reboot from time to time.  Perhaps there's another diagnosis/solution, but this has always worked for me.   

Only expensive, higher-end laptops seem to be safe from this problem, and on those you can tell when they're getting hot because the fan suddenly becomes audible and you feel the hot air coming out.

My Toshiba P25-s607 has only frozen two or three times in the two years I've had it. *Every* time was due to asking Ktorrent to run too many torrents.

---

### Post by warfacegod on 2010-06-20
> **crowhill said:**
> dust is most likely not a problem in my case as i got it cleaned only a few months ago.

under windows, my laptop does NOT become as hot! this must be a linux/ubuntu thingee.

A few months is longer than I care to let my laptop stay uncleaned. I clean mine every month or so.

---

### Post by crowhill on 2010-06-20
@ yossell

i just installed the nvidia dirvers. IT TOOK FOREVER TO DOWNLOAD AND INSTALL IT.

after it was done, i booted into windows (have a dual boot) the system starts to cool down after a while of using win vista).

then fired up ubuntu again. the UBUNTU logo at login is now much larger that without the nvidia driver. i'm not sure about the overall look but it feels bigger. much more important though, as soon as i fire up ubuntu, the fan starts to spin like crazy!

something strange is going on here!?!?!?!?

---

### Post by yossell on 2010-06-20
That does sound crazy and I don't know why you're having these problems. Installation of nvidia drivers was smooth and quick on both my laptop and desktop. On my laptop, it showed the correct resolution as default. On my desktop, I had to do some work to change the resolution.

Did the nvidia logo flash up? It appears for a few seconds when I boot up when the driver is installed.

I'm anxious about stressing your machine because heat is especially bad for them. Early on in my ubuntu experiments, my computer shut down, so hot it got. If you're feeling brave, can you run compiz with effects?

When you've booted up with nvidia loaded, can you select the nvidia X server settings? At the X server Display Configuration tab, you should have the chance to change resolution. Auto might be getting yours wrong for some reason.

Not graphics related, but make sure your chip is downclocked to keep heat low.

---

### Post by sandy8925 on 2010-06-20
most laptops with dual cores are pretty hot. when i was running vista the comp would do an immediate shutdown due to overheating. kubuntu also shuts down but doesn't just crash. it does a proper shutdown. the cooling in laptops just isn't enough for dual core cpu's. and now laptops with quad core cpu's are available. you can forget about running at cool temperatures and battery life for those.

---

### Post by yossell on 2010-06-20
sandy, that's true, but he's stated that he's not having the same degree of heat problems when he uses windows.

---

### Post by sandy8925 on 2010-06-20
are you sure you installed the correct drivers? did you check the power management,temperature etc. in the nvidia-settings program?

---

### Post by TBABill on 2010-06-20
Sounds like an incorrect nVidia driver. I would remove in Synaptic, then reinstall a different nVidia driver. That's one step to seriously cool the laptop. The open source drivers are not able to control heat on your GPU.

Secondly, as suggested earlier, enable CPU scaling. I have a 1.9MHz dual core AMD chip and it runs most times at 800MHz because I have it in "ondemand" mode, which limits CPU speed unless needed. My laptop went from running 70-85 degrees C to now running 47-60C. 

Those two items are now first priorities for me when installing another distro. I get the system cool then worry about other apps.

Do a search for scaling, ondemand, etc. on the forum. Also, the Ubuntu wiki has lots of great configuration info as well.

---

### Post by crowhill on 2010-06-20
the nvidia logo does not show up during boot. however, i can see and use the nvidia xserver settings menu. the indicated resolution is the best i can get. that should be fine. it appears, it's only the ubuntu logo at login that looks overly large.

i installed powertop. what can i do with it? 

i executed a few commands i found in the forum. here's the output:

```
[COLOR="red"]nvidia-settings -q all | grep Temp[/COLOR]
  Attribute 'GPUCoreTemp' (b:0.0): 56.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
  Attribute 'GPUCoreTemp' (b:0[gpu:0]): 56.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
```

```
[COLOR="Red"]sudo smartctl -a /dev/sda | grep Temp[/COLOR]
194 Temperature_Celsius     0x0022   100   092   000    Old_age   Always       -       47
```

```

[COLOR="Red"]cat /proc/acpi/thermal_zone/THM/temperature[/COLOR]
temperature:             50 C
```

right now, my machine has an ok temperature. however, i tried these commands earlier and the output was different. the second command showed 54 and the third 61 C. Is that normal?

i don't need compiz 3d flashy thingees. i just want a well running workhorse. i can't remember what i was thinking when i bought nvidia but it sure was stupid!

another reason why i didn't want to install the nvidia drivers is that it does not detect my vga and hdmi ports ...

---

### Post by yossell on 2010-06-20
Hi crowhill,

run 

sudo powertop

and follow its suggestions if you can.

I'm not sure from your final post how things are. Are you now happy with the temperatures? Is the resolution ok? are the drivers working? Is the fan running sensibly now?

It's normal for temperatures to fluctuate in the way you say: when I play chess programmes, the temps of the gpu rises because the heatsink is servicing both cpu and gpu, and can't shuttle heat away effectively if there's a lot of heat from the cpu too.

One note of warning: I don't think nvidia server settings gives an accurate reading of the gpu on my dell m1330 - the command 

nvclock -T

at a terminal is more accurate - and, on my machine, gives a reading 15 degrees higher that the server settings utility. But if you really are getting those temperatures, then you're doing well for that computer given you've not modded it. 

Though the 8400G has a known issue, my experience is that nvidia cards work well with linux in general.

---

### Post by Onesimus on 2010-06-20
You might want to take a look at this thread

[http://ubuntuforums.org/showthread.php?t=842775]("http://ubuntuforums.org/showthread.php?t=842775")

It's all about laptops overheating.  

It seems that some Ubuntu has a problem activating the fans correctly on some models of DELL laptops.

---

### Post by crowhill on 2010-06-20
it appears things are better now. i gave my laptop a rest (actually, there was a power outage so i basically had no choice) and the fan hasn't gone crazy yet. however, i'll keep an eye on it as it has alway been a bit "suspicious" on ubuntu.

there's one issue remaining though. maybe, i should start a new thred for that!?

my nvidia card isn't recognizing my vga and hdmi ports! i can't connect to a projector nor to the tv. that's kind of annoying ...

anyways, thanks a lot!!

---

### Post by TBABill on 2010-06-20
crowhill, if you have things installed correctly you can get your temps by typing 'sensors' into a terminal. That will output your temps in degrees C. I used it after changing my cpu scaling configuration to make sure my temps stayed ok. 

Your temps of about 60C are fine. My machine has limits of 99C but you'll be complaining of the heat long before things get that hot. At about 80C I could no longer handle having it in my lap (even with the vents and fan unobstructed).

---

