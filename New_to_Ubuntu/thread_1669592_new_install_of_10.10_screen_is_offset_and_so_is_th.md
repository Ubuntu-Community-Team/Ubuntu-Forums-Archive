---
title: "new install of 10.10 screen is offset and so is the mouse"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by shortrun on 2011-01-17
Any help please.
 
I have a PC with just ubuntu 10.10 installed.
The video comes off the mother board and uses nvidia drivers.
 
What I see is the screen seems shifted up a bit.  The bottom task bar is just barely visible and the top task bar is wider than it should be.
Other than this the screen looks totally normal.
The mouse works but I need to position it just a bit higher or above what I want to click on.
 
If I change the resolution the screen and mouse operation correct themselves sometines for very short time then go back to this offset discribed above.

---

### Post by Shane11 on 2011-01-18
I had the same problem. My Philips LCD monitor has a set up menu; one option is 'Adjust Screen Position'. It automatically fixed the problem for me.

---

### Post by Dutch70 on 2011-01-18
+1 I had the same problem & solution. Although it took me a while to figure out that it was actually...the monitor settings that had changed.

---

### Post by NightwishFan on 2011-01-18
I found that when I dual booted Windows and Ubuntu they would constantly shift the screen different from each other, if you have an auto button in the menu on the monitor as mentioned above, that will work perfectly.

---

### Post by shortrun on 2011-01-18
Thanks
I should have said the text inside the task bars is normal size, it's just the bottom one is cut off and the top has empty space.
I don't think it's the monitor setting, I have an old NEC Multisync 95.  It does not have any settings just the normal adjustments these old monitors have.
How could that effect the mouse operation.  I actually have to have the mouse pointer not on the box I'm clicking but above it by about 1/8 inch or 4 mm.

I entered this command in the terminal mode
sudo apt-get install nvidia-settings

Then I have to change the monitor resolution using "System"  "Preferences"  "Monitors"
And now the monitor and mouse operation are normal and stay good until I restart the computer.  Then I have to go through this changing the resolutions. 
It does not matter what resolution I set it too.

---

