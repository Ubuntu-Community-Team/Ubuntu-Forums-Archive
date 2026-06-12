---
title: "mtink will not display results"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Scunnered on 2009-05-04
When browsing through the help I saw that the above would display the contents on my ink cartridges so I duly downloaded it only to find that it would not properly work.

What would appear to be the display shows up but does not display the contents and although there are varying boxed at the foot of the display they are either greyed out or do not function.  Additionally an error message is displayed and reference is made to documentation that I am unable to access.

I append screen shots for information and ask how may I resolve matters.

---

### Post by gj_clt on 2009-05-04
I use to use an Epson printer and if I remember correctly mtink ran from within a terminal using the sudo command. I think there was also a problem with users having to belong to a certain group but I'm not sure about that.

---

### Post by Didius Falco on 2009-05-04
> **Scunnered said:**
> When browsing through the help I saw that the above would display the contents on my ink cartridges so I duly downloaded it only to find that it would not properly work.

What would appear to be the display shows up but does not display the contents and although there are varying boxed at the foot of the display they are either greyed out or do not function.  Additionally an error message is displayed and reference is made to documentation that I am unable to access.

I append screen shots for information and ask how may I resolve matters.

Looking at the second screen shot, it looks like you, as the user, must be a member of the "lp" group.

To add yourself to this group, go to **System/Administration/Users and Groups** and open it up. After you **Unlock** it with your password, click the **Manage Groups** button and look for a group named **lp**. Highlight it, click the **Properties **button and tick the box next to your username, and any other users that will need the same access. 

Click **Okay**, close all the windows and try it out.

I hope this helps...

---

### Post by Mark Phelps on 2009-05-04
There's an easier way to do that ...

Presuming your username is "joe", you would just open an terminal and type "sudo adduser joe lp".  This adds the user joe to the lp group.

To check if that worked, from the same terminal, type "cat /etc/group | grep lp".  You should get a reply something like "lp:x:7:joe:

---

### Post by Didius Falco on 2009-05-04
> **Mark Phelps said:**
> There's an easier way to do that ...

Presuming your username is "joe", you would just open an terminal and type "sudo adduser joe lp".  This adds the user joe to the lp group.

To check if that worked, from the same terminal, type "cat /etc/group grep lp".  You should get a reply something like "lp:x:7:joe:

Thanks Mark. I learn something new every day if I'm not careful ;)

---

### Post by Scunnered on 2009-05-04
My thanks to you all for your assistance.

I had a look at Mark's suggestion and it appeared to work but when applying the second instruction it displayed a lot of info ending with

"cat: grep: No such file or directory

cat: lp: No such file or directory
"

Tried mtink but still same error message.

Went to **Didius Falco** when looking for lp in manage groups the only thing that I could find was a group lpadmin and on opening properties found that I was listed.

Tried again but still no joy even after adding root to lpadmin.

Where do we go from here?

---

### Post by Didius Falco on 2009-05-04
You can create that group from the Users and Groups management utility, so just create it and add yourself to it, then log out and back in. It may require a reboot.

I went and had a look at that util, and it's a bit long in the tooth - from before I started using linux, so it's possible that was a group in widespread use earlier in the decade that isn't created by default anymore.

On Edit: I just did a search and I already have an lp group, but it isn't showing up in the Users and Groups utility. I'm off to see what I can find out - meanwhile, hold off on creating it, though I suspect it wouldn't let you anyway...

Hopefully, that'll get you fixed up.

---

### Post by Didius Falco on 2009-05-04
Run this command and post the output: 

```
cat /etc/group | grep lp
```

---

### Post by Scunnered on 2009-05-04
**Didius Falco**

THis is the result of your request.

"ian@ian-laptop:~$ cat /etc/group | grep lp
lp:x:1001:ian,root
lpadmin:x:106:ian,root
ian@ian-laptop:~$"

I clicked in error on mtink when going for the terminal and now mtink is showing something different. But not a lot as the next button does nothing.

---

### Post by Didius Falco on 2009-05-04
Have you rebooted since you added yourself to the lp group? If not, do so.

---

### Post by Scunnered on 2009-05-04
**Didius Falco**

Yes I have done that before I responded to your request.

This is getting a bit like anyone for tennis?

---

### Post by dnairb on 2009-05-04
When you start mtink, click on one of the ports listed, then click "next" (it is asking you to specifiy a port)

---

### Post by Didius Falco on 2009-05-04
> **Scunnered said:**
> **Didius Falco**

Yes I have done that before I responded to your request.

This is getting a bit like anyone for tennis?
  
<G> Yes, it is - though I'm starting to feel a bit more like I'm looking for a needle in a haystack.

On the screen that you posted the last screen shot of, did you select one of them before pressing next? Did you start mtink with root privileges?

---

### Post by dnairb on 2009-05-04
> **Didius Falco said:**
> ...Did you start mtink with root privileges?

I believe you don't need need root privileges to start mtink.

---

### Post by Didius Falco on 2009-05-04
I'm at the grasping for straws stage at this point - I'm actually hoping he never selected a port...

If you are familiar with this mtink, please, step in - I've only got one bullet left in my gun. [-o<

---

### Post by Scunnered on 2009-05-04
Right folks I am now in "the Scream" mode.

I have got in the habit of using the post information from the screen and applying what ever I have been told.  I was a bit quick in doing this as I had not fully read the post as I was asked to hold off doing things yet.

I went back and changed things back. Now I can't return to the last screen shot. Fortunately enough I did not click on a port.

When I use mtink now I revert back to the original screen shots.

**Didius Falco**

What ever you do please do not use your last bullet on yourself. 

I will leave matters with you all as I have to go out in the next 10 minutes and will not get back until about 22:00 hours.

Once again my thanks to you all for your kind assistance

---

### Post by dnairb on 2009-05-04
> **Didius Falco said:**
> I'm at the grasping for straws stage at this point - I'm actually hoping he never selected a port...

If you are familiar with this mtink, please, step in - I've only got one bullet left in my gun. [-o<

I have used Mtink for my Epson R220 quite flawlessly since Gutsy. I'll try to remember the steps:

It is essential that the users who will use mtink are in a user group called lp ("small "ell" small "pee"). This group needs to be created as it doesn't actually exist in Ubuntu (lpadmin does, but this is a different group).:

System -> Administration -> Users and Groups
Click "unlock", enter user password, click "Manage Groups" then "Add Group". Call it "lp" and tick users that will use mtink.
I think that rebooting is necessary after doing this.

I found it easier to edit a file called .mtinkrc directly rather than configure mtink from itself.

The file .mtinkrc is in your user directory (open your hom directory and press "ctrl-H" to show hidden files). Open .mtinkrc in text editor and edit it. Mine looks like this:

> BROWSER: 
AUTODETECT: no
MINIHELP: yes
PRINTER: Stylus Photo R220
PORT: /dev/usblp0

The port name is usb "ell" p "zero"

You may have to change the port to **/dev/usb/lp0** and, of course, the printer name to your own (I don't think this really matters, as I think it is just the window title for when mtink is started)

Save .mtinkrc, ensure your printer is on (I know, but I've done this before!) then start mtink [Applications --> Accessories --> mtink]

If I have remembered everything, this should work.

---

### Post by Didius Falco on 2009-05-04
I got him through the create the group, add himself part, but the editing the configuration file part need the touch of someone that is or has actually used the program.

+1 to dnairb for the crucial help

+2 to Scunnered for sticking with it lo these many hours

Scunnered,

Don't worry mate. I survived the Smartmodem 300 bps blinding (as in you get old and go blind waiting for a file of any real size to download) speed. I survived Windows from 3.0 through XP. Anyone who thinks this could get me to top myself has another mtink coming. ;-) 

(and you thought vaudeville was dead...)

---

### Post by Scunnered on 2009-05-04
I have returned and am still in bother. 

I went back over the information provided by **dnairb** and confirmed that the lp properties were set as described.  Even took the trouble to remove mtink and re-install in case there were problems there.  Tried again only to find that I have now the lost screen shot.

Scratched wood and went looking for the hidden file mtinkrc and am still looking for it.  I selected places > home folder and clicked the up arrow twice and selected view and hidden files NOTHING.  Tried more up arrow till I found user and again view and hiden files NOTHING.  You are doing an extremely good job of hiding this file. 

Would chanting come out, come out where ever you are have any effect ?

I have taken the download from within Ubuntu so am at a loss as to what is going on.  

I am giving close consideration to asking **Didius Falco** for his gun as if this hidden file has not broke the camels back **his pun surely has** !!!!

Once again I attach the screen shots and would ask should I this time click on the

"/dev/usb/lp0" or what do you suggest.

PS Going back to Applications > Accessories > there are two items displayed. There is mtink and mtinkc each when clicked produce the Epson Utilities screen shot.  Dont know if this helps or hinders

---

### Post by dnairb on 2009-05-04
Places --> home is enough to show your home directory.

If the .mtinkrc file isn't there, it may be that it is not created until mtink has been configured and is running.

So... let's try to create the file first. (or edit it if it is there)

Close mtink (if it's still running)
Open text editor and type:

> BROWSER: 
AUTODETECT: no
MINIHELP: yes
PRINTER: **Name of your printer**
PORT: /dev/usblp0

save as .mtinkrc in your user directory

Then try running mtink again (silly, but easily overlooked point: make sure the printer is connected and is on)

---

### Post by Mark Phelps on 2009-05-04
> **Scunnered said:**
> My thanks to you all for your assistance.

I had a look at Mark's suggestion and it appeared to work but when applying the second instruction it displayed a lot of info ending with

"cat: grep: No such file or directory

cat: lp: No such file or directory
"

That's because I made a mistake in the command ...

The correct command is "cat /etc/group | grep lp" -- notice the "pipe" between the cat command and the grep command.  Sorry about that -- typed too fast and didn't go back to check it.  Fixed now.

I too found that manually copying a saved .mtinkrc file was the easiest way to get mtink working from upgrade to upgrade.

Finally, you do realize that the config file is a "hidden" file -- as indicated by the leading period.  Nautilus does not display these by default.  You have to enable that in order to see the file.  So, it may actually be there but you're not seeing in in Nautilus.

---

### Post by Scunnered on 2009-05-04
You will think that I am thick (if you are not doing so now) but how do I save this instruction in user?

I was initially offered my own file ian.  Could not find a way to browse to user. So saved in ian thinking I could copy this to user.  Clicking on file and using copy did not let me do so when I then used the uyp arrow from ian to take me to user.

What am I doing wrong?

---

### Post by dnairb on 2009-05-04
My apologies... when I said user, I meant your home directory.

---

### Post by Scunnered on 2009-05-04
OK folks - panic over. Marks post came through when I was posting mine. 

Used his details and as I was going to reply to him got the reply about the home directory.  Went there and found that there was both a hidden file and a backup of it in home . ian. 

Restarted saystem and checked mtink and everything works a treat. Its amazing that what would appear to be such a simple operation turned into a panto.

My sincere thanks to each and everyone of you for all your kind assistance. Award yourselves a large libation.

---

### Post by Didius Falco on 2009-05-04
You are welcome. Besides, if I ever get an Epson printer, I'll know what to use to track my color cartridges and how to set it up - or at least how to go back and find it.

But no libations for me. Why, I never touch the stuff!! 
:---)

---

### Post by john geary on 2009-05-20
Didius got mine 10 minuites ago working by suggesting two methods,I tried both, the one that worked was by using the terminal commands to join the group lp(lower case).when the mtink screen came up and part of it was greyed out I had to go into PREFERENCES at the bottom left and change to /dev/usb/lp0 (try the other without the slash)dont forget to turn on the printer , log out and restart.

---

### Post by arvevans on 2012-01-18
**mtink**, **mtinkc**, and **ttink** all seem to be broken in 11.10 if you have a USB connected printer.  They will only allow configuration for serial and parallel port printers, but not USB printers.  

**escputil** works for me in 11.10 with a USB connected Epson CX-7400 all-in-one printer.  You do have to use the -u option for newer printers.

---

### Post by Mark Phelps on 2012-01-18
mtink DOES work in 11.10, even for USB-connected printers.

It's just that with 11.10, you have to load a kernel module -- one that was loaded by default in previous Ubuntu versions.

Sorry, not at my Linux box, so I don't have that info, but I will check later tonight and update this thread.

---

### Post by ubudog on 2012-01-18
This is an old thread, it would be best to start a new one.  

Thanks,
ubudog

---

