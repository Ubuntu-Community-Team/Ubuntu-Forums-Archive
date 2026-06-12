---
title: "Attachments to new mail in Yahoo!mail"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by dstjohn on 2009-12-27
I am running Ubuntu 9.10 and using Yahoo!mail on the web in the Firefox browser.  When I start a NEW message the second button at the top of the new message screen (next to 'SEND' and before 'save Draft') should be the ATTACH button.  

When the new mail window is started it flashes up ATTACH and then it disappears in favor of a blank button; there is a 'pop up' message that says EDIT ATTACHMENTS, but the button does not work!

When I do the same thing in Windows XP - Firefox, the ATTACH button works normally.

is there a FIX for this problem in Ubuntu?
how would i find it?

:confused:

---

### Post by zoglesby on 2009-12-27
I was not able to reproduce this issue, are you running any extensions that might be causing this?

---

### Post by Captain_tux on 2009-12-27
I've tried it also and don't have any problems... doesn't really sound like an Ubuntu problem to me.

How much RAM do you have? Sometimes I get a window in which I don't see all the boxes/options for until I mouse over it, then again, I have a ton of apps open.

---

### Post by Captain_tux on 2009-12-27
Also, do you have NoScripts running? NoScripts will kill all the Java scripts applets & functionalities that come with web pages...

---

### Post by dstjohn on 2009-12-27
> **zoglesby said:**
> I was not able to reproduce this issue, are you running any extensions that might be causing this?

***
interesting;
my Ubuntu is pretty vanilla.
i'll have to keep checking.


thanks

---

### Post by jrothim on 2010-02-17
Hi - 

I have the same problem, running Ubuntu 9.10 and Firefox 3.5.7.  The Yahoo! Mail "Attach" button does not do anything.

I also noticed similar issues with other websites that open additional windows with buttons.

For example, the Mathworks Matlab download agent also has the same problem.  And the MobileMe (iDisk) file uploader window has the same issue when you try to click the "Choose..." button.  (i.e., nothing happens.)

I installed Java and have all Java features enabled in Firefox.  I also am not blocking pop-up windows.  And I am not running the NoScript add-on.

I just installed this Ubuntu/Firefox system recently.

If anyone has any tips, please let me know.  Thanks!
Jeff

---

### Post by jrothim on 2010-02-25
Hi All - 

The problem on my system appears to have been resolved when I disabled the GNU Shockwave Flash player (Shockwave Flash 10.1 r999 Gnash 0.8.6) in Firefox.

I disabled that add-on using the firefox preferences.

When I then installed the Adobe Flash Player, the Yahoo mail attach button works.

You can get the Adobe Flash Player plugin at the download link location for Adobe below.  I selected the .tar.gz file for linux.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then I copied the libflashplayer.so file to the firefox directories as specified [at this link]("http://www.linuxquestions.org/questions/linux-newbie-8/trouble-extracting-and-installing-adobe-flash-player-785465/"):

% sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/.
% sudo cp libflashplayer.so /usr/lib/mozilla/plugins/.

Don't forget to restart the browser. :)

This also fixed the problem on the mobile me website ([http://www.me.com/idisk/](http://www.me.com/idisk/)) where the upload and download buttons would not bring up the file-selection windows.

Jeff :)

---

### Post by mErchamion on 2010-11-24
@jrothim  Worked for me on Ubuntu 10.10, but why does it happen? I had never had any problem previously.

---

### Post by tjwilli on 2010-12-21
Thanks. Disabling GNU Flash player worked for me. I haven't tried installing the Adobe player yet.

---

