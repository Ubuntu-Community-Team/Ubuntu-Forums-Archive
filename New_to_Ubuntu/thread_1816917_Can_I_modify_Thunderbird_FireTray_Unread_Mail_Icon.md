---
title: "Can I modify Thunderbird FireTray Unread Mail Icon?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-08-02
Not a big issue...

I have been using FireTray for a long time & like it a lot.
Previous versions had a pretty ugly icon which displayed the number of new or unread mails on a bright cream background.
The latest version (FireTray 0.3.1) which just arrived, has replaced the bright cream background by a more discrete gray.
Less ugly - but not as effective!

Previously, I couldn't avoid noticing a had unread mail (the whole object of installing FireTray...).
Now, I have to consciously check.

In FireTray properties, I can choose the color of the unread messages number & I have tried a lot of them, but that does not make much difference.

Is there any way I can get back to the ugly cream background, or customise the background, or make the icon more noticable?

Thank for any suggestions - even just locating the icon in the files!

---

### Post by JGeraci on 2012-02-09
You can do this somewhat easily.  Maybe it's a hack, but it worked for me.
- First create/locate the icon you want to use in place of the nasty gray one.  It needs to be a .png.
- Next, open the xpi file by clicking on it (this opens the compressed file for me in a folder/file form, which is good.  The file I used is firetray-0.4.0b2-sm+tb+fx-linux.xpi.
- Navigate to chrome->skin.  You should see a file called blank-icon.png.
- Replace blank-icon.png with your new one.  For instance, you can drop your new icon here, delete blank-icon.png and rename the new icon to blank-icon.png (or however you want to do this step)
- Close the 'xpi' window/file
- Remove the old firetray add-on in Thunderbird
- Install your newly modified firetray xpi file (click Tools->Add-ons and the icon near the search bar, then Install Add-on From File)

And you should be good to go!

Cheers.

---

### Post by 2CV67 on 2012-02-18
Thanks very much, JGeraci, for your complete, detailed & successful solution!

It took me rather a long time before trying it - sorry! - but it works perfectly & the result is a big improvement for me.
I now have a plain bright yellow background with the unread mail count dark red on top - unfailingly catches my eye.

The only slight difficulty I encountered was that nothing I tried wanted to open the .xpi file, but I temporarily renamed it to .zip for modifying, then back to.xpi for installing.

Thanks again!   :D

---

