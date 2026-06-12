---
title: "New to Linux - Graphics card not recognised?"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by limatwo on 2010-01-28
I'm new to Linux and decided to try Ubuntu to breathe some life into this well worn machine (current specs below). I've spent a couple of weeks, on & off , trying different things & lurking on this forum (thanks in advance to all the gurus who spend their time helping with problems).
I'm writing this using ubuntu 8.04, so in most respects, the installation has been a success, but this is the most recent version I could get to recognise my vid card.
I'd rather use a later version, but I appreciate the difficulties supporting older hardware. If an easy solution isn't obvious, I'd be happy with this installation except for the following:
1/ I understand that 8.04 becomes "obsolete" when the next LTS is released, 10.04.  Is the problem I experienced in 9.10 likely to be carried over in 10.04, and if so, what issues are there with my continuing to use 8.04?
2/ The main reason for using a graphics card is to use dual monitors. At the moment 8.04 seems to be picking up one graphics output or the other, but not both.

OK, here's what I did in detail:
Before inserting a vid card (so using the onboard graphics), I loaded Ubunto 9.10 from iso burned to cd- very impressed 'cos It was up & running in no time. It saw my internet (ISDN hub) right away, and even networked to a similar spec Widows PC.
But then:
I installed an ati graphics card (similar spec to the one listed below) and now 9.10 wouldn't boot. When I tried to boot from the 9.10 live cd, it got thru the language choice & options menu, but then just scrolled pages of errors before the machine froze.
As I thought it was (obviously?) a graphics card driver problem, and I also thought I'd read that linux likes nvida better (????)  I changed to the card listed below. Same result.
I then tried ubunto 9.04, and that went as far as the splash screen with the osscilating progress bar, before also freezing.
I thought it was worth trying ubuntu 8.04 LTS - and it worked fine with the nvidia card! I installed 8.04 ( but this time to dual boot with win xp, just "in case" ). I have installed my first progs, was prompted to load a nvidia proprietary driver (which improved graphics), and again accessed the net and local network with just a little trial & error.

I'd appreciate any insights.

System details:
HP Compaq dx200MT
2.66GHz  750mb ram
hd 40Gb - win xp
hd 160Gb data
hd 20Gb Obuntu 8.04
graphics card nvida Geoforce FX5200 (pci 128mb, Dvi, D-sub, TV-out)
onboard sound

---

### Post by clhsharky on 2010-01-28
HI

Hardy 8.04 is supported till 4/11, "obsolete" I dont think so.
Old - little bit, but not as old as your hardware. Should be fine.

Sharky

---

### Post by limatwo on 2010-01-28
Thanks Sharky

So it's just that support for this (these) vid cards was dropped after v8.04?

Any ideas about getting dual monitors working?
Win xp just finds them at boot up no probs. In Ubuntu 8.04, both screens mirror the log in & splash screens right up until the desktop displays - then one of them goes to standby. Each is plugged into a different output from the same card.

Rgds limatwo

---

### Post by audiomick on 2010-01-28
Have you run
```
sudo nvidia-settings
```
the setup thing.

---

### Post by limatwo on 2010-01-28
> **audiomick said:**
> Have you run
```
sudo nvidia-settings
```
the setup thing.
Michael, this is what I get

limaed@compaq01:~$ sudo nvidia-settings
sudo: nvidia-settings: command not found

---

### Post by audiomick on 2010-01-28
Thats a bit odd.
have a look at
system> administration> hardware drivers
and see if the nVidia driver is activated.

---

### Post by limatwo on 2010-01-28
> **audiomick said:**
> Thats a bit odd.
have a look at
system> administration> hardware drivers
and see if the nVidia driver is activated.
Hi Michael
The nvidia accelerated graphics driver is activated and shown "in use"
Attempting to u/load a s/shot

Rgds  Ed

[IMG]http://ubuntuforums.org/album.php?albumid=1647&pictureid=5572[/IMG]

---

### Post by overdrank on 2010-01-28
> I thought it was worth trying ubuntu 8.04 LTS - and it worked fine with the nvidia card! I installed 8.04 ( but this time to dual boot with win xp, just "in case" ).
If you have installed 8.04 you will have to install the nvidia-settings as the nvidia drivers did not include the settings in Hardy 8.04. :)

---

### Post by limatwo on 2010-01-28
> **overdrank said:**
> If you have installed 8.04 you will have to install the nvidia-settings as the nvidia drivers did not include the settings in Hardy 8.04. :)
Thanks for the input Overdrank, but I'm sorry, I don't know what that means.

"out of the box", 8.04 worked with the nvidia card. I was prompted to d/l the accellerated driver, which I did, and which is shown as "in use" - and the screen display did improve after that.

Rgds  limatwo

---

### Post by audiomick on 2010-01-28
overdrank is right, I can remember doing that in the dark and distant past, now that he mentions it.

Do
```
sudo apt-get install nvidia-settings
```
or open the synaptic package manager, search for "nvidia-settings", mark it for installation and apply.

---

### Post by overdrank on 2010-01-28
> **limatwo said:**
> Thanks for the input Overdrank, but I'm sorry, I don't know what that means.

"out of the box", 8.04 worked with the nvidia card. I was prompted to d/l the accellerated driver, which I did, and which is shown as "in use" - and the screen display did improve after that.

Rgds  limatwo

Ok sorry. :)  If you want to use the dual monitors you will need the nvidia-settings to set them up. You can use the terminal located under applications, accessories. Enter the command ```
sudo apt-get install nvidia-settings
```
After that is completed then you can use the command ```
gksu nvidia-settings
``` then you can setup the dual monitors and adjust resolution and such. :)
Edit: also another tool that was included in Hardy 8.04 was ```
gksu displayconfig-gtk 
```

---

### Post by max-power2717 on 2010-01-28
Hi,

I was just working on a similar problem with Hardy 8.04. I replaced an ati card with an nvidia fx 5200 card and my window manager display was terrible (640x480).

I found some instructions that recommended installing nvidia-glx and nvidia-settings (I see nvidia-settings has already been recommended above). After install and restart, window manager was still in 640x480 mode. I started nvidia-settings, and it recommended running nvidia-xconfig which I did. See instructions I followed [COLOR=Blue]**[here]("http://www.ubuntuhowtos.com/howtos/replace_ati_with_nvidia")**[/COLOR].

After another restart, the window manager was still in 640x480, but I was able to start nvidia-settings. Under XServer Display Configuration in nvidia-settings, I chose "auto" for Resolution (as that was the only other entry available other than 640x480). Restarted gdm again, and my resolution was fixed (was then the native res of the screen).

One final issue that I had (and solved quickly with google) was that all my windows opened up in the new resolution with no title bar, making it awakward to move and close windows. This is apparently an issue with the nvidia driver. The first solution I tried worked.. it involved adding the following option lines to the device section of xorg.conf:```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```The steps I followed are from [COLOR=Blue]**[this page]("http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/")**[/COLOR].

This pretty much solved my issue. I have the feeling that my window borders aren't being displayed properly at this time, but that's not a problem for me so far. The other solution I found about the window titlebar issue with the driver used was to manually download and install an alternative version of the driver. Since this simple soution worked well enough for me, I didn't bother with the alternative driver. 

Hope this information helps.

---

### Post by limatwo on 2010-01-28
Thanks to all for the help.

I d/l and installed nvidia-settings, and I can See what I want, but am struggling a bit to get it!
Both monitors show in the nvidia-settings window (shot), but when I try to apply the option for "separate x screens" (shot03), I get the error (shot04). The machine won't let me to "save to the x config file" (which is what I guess I need to do(?)), and after a reboot, we revert to the second monitor being disabled and a blank screen.

I have to work tomorrow (today), so I'm going to wrap it up for the night, and I'll have a look at the other suggestions above tomorrow, & post when I've done that.

Thanks again & rgds limaed

---

### Post by audiomick on 2010-01-29
Hi.
If sounds confusing perhaps, but you don't want the option "seperate X screen".

You just want to have your desktop spread over two monitors, right?
You need the option "Twin View". That is a proprietary nVidia solution. It only uses one screen, in the sense of an x server screen, and spreads that across the two monitors. So if you have 2 1280x1024 monitors side by side, Twin View will create a screen of 2560 x 1024 and put half on each. If the same two monitors were one above the other, the screen would be 1280 x 2048.

My two monitors are 1024 x 768 on the left, and 1280 x 1024  on the right, so the screen size is 2304 x 1024, i.e. as wide as the two together, and as high as the higher.

---

### Post by limatwo on 2010-01-29
Hi all & happy to report I'm writing this on my secondary screen. All seems to be good, with ubuntu desktop/toolbars on the primary monitor, and empty space on the secondary, to where I can slide windows over from the desktop with the mouse. Ms Jolie seems to want to drape herself over both displays as if they were one, but I'm sure I can come up with a background that will lend itself to being tiled!

It was a bit trial & error, using settings in:
<nvidia-settings>
and also in:
<gksu displayconfig-gtk>
in order to 1/ activate both screens, and 2/ get the correct resolution.
Setting the resolution was difficult. After I consistantly got both screens to work, one or other initially displayed at max 800x600, even though indicating 1024x768. I re-set the resolution controls and rebooted so many times that I really don't know what combination worked.

Thanks again for the assistance. I think I'll be asking for more in the coming weeks.
Rgds  limatwo

---

