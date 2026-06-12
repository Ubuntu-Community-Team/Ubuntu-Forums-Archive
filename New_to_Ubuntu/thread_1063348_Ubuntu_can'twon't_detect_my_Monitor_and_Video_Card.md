---
title: "Ubuntu can't/won't detect my Monitor and Video Card."
date: 2009-02-07
forum: New to Ubuntu
---

### Post by nicesocks on 2009-02-07
i'm having an issue on boot up.  
when i start up i go through the steps we normally see;  bios loading, a brief flash of the mobo's splash, grub loading, then the screen with the ubuntu logo and a sliding bar going back and forth.  (by the way, this specific screen renders in 1280x1024)

then the screen is loaded with about ten lines of text, the exact details of which escape me but i can retrieve them then next boot up.  this flashes three times.

and then the screen goes black with a "X" shaped cross hair in the middle.  and a message pops up telling me that ubuntu can't detect the monitor and video card.  it permits me to do this manually, by choosing the "configure" option.

so i click configure to find a monitor...  um... i don't know it's model, but it's a dell, the flat screen kind it seems everyone has.  so i choose a LCD that has the aspect ratio i'm looking for.
and then i click the tab to select my video card.  it's a nvidia9800gt and i know people are having issues with this one.  well, i can choose nvidia but none of the nvidia models are like the one i have.  i've also tried this with both ubuntu drivers, and proprietary drivers.  in fact, i've used the synaptic to remove my old drivers and replace them with the 1.80 drivers.

i then tell it to "test" and it reveals a screen that asks if i want to keep these settings.  i say yes, and proceed to load.

it then loads up in 800x600.  granted, this could be worse, but it's a hideous way to use my machine, and i would much rather enjoy having the extra space a 1280x1024 resolution offers.

i've gone into my hardware drivers, and ensured that the nvidia drivers are selected and "in use."  and then it asks for a restart, and we get to go thorough the process all over again...

how do i fix this?  i'll happily post any information that's needed.  i'm used to ubuntu, but i won't claim i'm savvy with it.  so you might have to hold my hand through terminal runs... ;)

---

### Post by Unanimated on 2009-02-07
Alright, I'm having issues with my NVIDIA card as well. It's something in the new kernel that the hardware drivers offered in Synaptic just... well, they don't work. What may (note 'MAY,' this hasn't fixed mine yet) fix your problem is to go to the NVIDIA site and click "Download Drivers." It will automatically select your OS and card. Download the driver to your desktop, and I recommend renaming it 'driver.run' and moving it to your Documents. Now, write this stuff down, as you'll only have a GUI for 1 step.
Press Ctrl+Alt+F1, then put in your username and password. Note that your password won't show up, but it's being put in - don't worry.

```
sudo /etc/init.d/gdm stop
(password)
cd Documents (assuming you moved it here)
sudo ./driver.run (assuming you renamed it this)
Then go through the setup process. At the end, hit Yes
sudo /etc/init.d/gdm start
```

While this will give you the resolution you want, it won't let you have 2 screens - again, a relatively major bug with the new kernel. I can't even guarantee these, as I have a 6200 GeForce, but they should work.

---

### Post by abyssius on 2009-02-07
If you connect your LCD to your Video card using an analog VGA port, you have to identify it as a CRT. If you use a DVI or another digital connection, then selecting LCD is okay.

---

### Post by nicesocks on 2009-02-08
@unanimated

ok, so i downloaded the driver i needed.  renamed it driver.run.  moved it to my "Documents" folder.
then used ctrl+alt+f1
typed in my username, then my password.
typed in ```
sudo /etc/init.d/gdm stop
(password)
cd Documents
sudo ./driver.run
```
and this was my result: ```
sudo: ./driver.run: command not found
```
did i do this right?

oddly enough, i logged in when i got home and had my resolution set up correctly...  but i don't have access to my 3d capabilities.  a real pity...  but at least not such an eyesore.

~~~

@abyssius 

my monitor is connected into an adapter that connects it into a different port than i'm used to seeing.  mind you, my old machine had a very different port than what this one has.  i don't know what they are called.

---

### Post by Megapocalypse on 2009-02-11
Hey, 

I'm having the same problem, but in the demo mode. The box comes up telling me it's in low-res mode and that it cannot detect my video or monitor. I've tried clicking on the configure option, but after that, I get the message to restart, then the same thing over again. I would really like to preview this before I install and found out I've totally kicked myself in the rear. 

I DO have a blank computer with a botched install of Win98 to play with, but unfortunately, I have no clue what the video card in it is.

The card in mine is a S3 Trio 64V2-DX/GX with a CTX VL700 monitor, if that helps.

EDIT:

I chose low graphics mode on the main menu, but now I'm getting a totally different error. I found an old thread on it, but I can't understand any of it. Dx Help please? I'm not very technical.

> The following error was encountered. You may need to update your configuration to solve this.

(EE) VESA (0): Unknown EDID
Version 0

---

