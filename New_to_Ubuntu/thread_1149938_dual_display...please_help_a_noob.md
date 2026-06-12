---
title: "dual display...please help a noob"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by dam66 on 2009-05-05
Just built a new machine & have installed Ubuntu 9.04    (clean install)
This is my first Linux experience...noob
(have had enough of a good friend making fun of me & my Win-probs...lol)

(thought I had lost stuff in a cross country move and recently found it ... so the components are 3 yrs old, but were still in the box)

abit Fatal1ty AN9 32X motherboard
AMD A64 X2 4200+
EVGA e-GeForce 7600 GT  (GDDR 3 - 265MB)
corsair DDR2 XMS2 pro series  2gig


I'm trying to use dual display...
I go to  System / Properties / Display

I get:
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Yes

opens the nvidia x server settings ...
-------------------------
Under 
GPU 0 - (GeForce 7600 GT)
it lists
CRT-0-(ViewSonic A70)
CRT-1-(Dell UltrascanP990)


in:
X server display configuration   ...   layout
shows that there are 2 monitors
the ViewSonic & the Dell (says Disabled) 


I click the Dell    goto configure
pop-up window:  "Configure Display Divise" gives me the 3 options of;   
Disabled (checked)
Separate X screen (requires X restart)
TwinView
    OK / Cancel

I check Separate ...   hit OK
then hit Apply
 pop-up:  Cannot Apply
The current settings cannot be completely applied due to one of the following reasons:
-The Location of an X screen has changed.
-The location type of an X screen has changed.
-The color depth of an X screen has changed.
-AN X screen has been added or removed.
-Xinerama is being enabled/disabled.

For all requested settings to take effect, you must save the configuration to the X config file and restart X server.

    Apply What Is Possible  /  Cancel

I hit Apply

pop-up:  Your current changes to the X server display configuration may no longer be applied due to changes made to the running X server.

You may either reload the current X server settings and lose any configuration setup in this page, or select "Cancel" and save your changes to the X configuration file (requires restarting X to take effect.)

If you select "Cancel", you will only be allowed to apply settings once you have reset the configuration.

   Reload current X server settings  /  Cancel

so I hit Cancel
then click "Save to X Configuration File"

pop-up: Save X Configuration
Show preview...(button)
(box) /etc/X11?xorg.conf       [Browse...]

(checked box) Merge with existing file

        Save / Cancel

I click Save

pop-up: 
 Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.
     
     OK (button)


tried the last step with the "Merge with existing file" box uncheck & got the same message



Where am I going wrong ?????


Please Help   :-)
Darin
dam66

---

### Post by stringkarma on 2009-05-05
Sounds like a permissions error to me. The NVidia configuration program is trying to write to your /etc/X11/xorg.conf but can't. 

Try instead, Alt+F2

and run 'gksu nvidia-settings' (without the '')

which (if I have my command correct) should run the configuration program with the proper permissions (enter your administration password when prompted)

Hopefully this helps.

(When you change the file you might need to restart the X server, which is most easily done by restarting the computer)

---

### Post by dam66 on 2009-05-05
This place is as good as I was told  :D
Thanx so much for the quick reply !

I'll try what U suggested & let U know

:D
dam66

---

### Post by beastrace91 on 2009-05-05
Running the nvidia settings in sudo is exactly what you need to do, just as an fyi selecting "twin view" will not require and X restart and thus u can do it with out running in sudo/restarting

~Jeff

---

### Post by lego126 on 2009-07-30
I had the same problem and just got it to work Great answer, and Thanks a bunch, just one more thing... Should I save these settings to my x config file?

---

### Post by pedro3005 on 2009-07-31
I guess, if you want them to stay and not be reseted.

---

