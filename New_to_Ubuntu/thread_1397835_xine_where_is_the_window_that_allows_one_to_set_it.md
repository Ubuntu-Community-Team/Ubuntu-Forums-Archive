---
title: "xine where is the window that allows one to set it up&gt;"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by senorian on 2010-02-03
Another poster was advised to check "system settings"; but there is no such entry (U9.10) as "system settings".
Not even under "menu"
Thanks

---

### Post by warfacegod on 2010-02-03
> **senorian said:**
> Another poster was advised to check "system settings"; but there is no such entry (U9.10) as "system settings".
Not even under "menu"
Thanks

You'll need to be more specific than that.

---

### Post by senorian on 2010-02-05
When I click on this url:
[http://radio.zvezdelin.net/](http://radio.zvezdelin.net/)
to listen to music the whole screen is filled with th word XINE.
I would like to either change to a different audio app. or modify xine so that I can see a small window that gives me details about the music that is playing.
Previously the site would open with Mplayer but would keep caching forever.
In attempting to change from Molayer I somehow got Xine.
I seem unable to get out.
Thanks for your quick reply

---

### Post by warfacegod on 2010-02-05
See attachment.

---

### Post by senorian on 2010-02-05
I can get to xine by clicking "sound and video" which brings up another windw with xine the last on the list; as your screenshot shows.
But clicking on the xine button brings up:

Could not launch 'xine'
Failed to execute child process "/home/jan/Climate_Change.pps" (Permission denied)

How do I either get rid of xine (and get some other app to play the music) or modify xine.
Thanks
ps wth does climate change have to do with anything?

---

### Post by warfacegod on 2010-02-05
> **senorian said:**
> I can get to xine by clicking "sound and video" which brings up another windw with xine the last on the list; as your screenshot shows.
But clicking on the xine button brings up:

Could not launch 'xine'
Failed to execute child process "/home/jan/Climate_Change.pps" (Permission denied)

How do I either get rid of xine (and get some other app to play the music) or modify xine.
Thanks
ps wth does climate change have to do with anything?

If I'm not mistaken .pps is a Powerpoint Presentation.

Right click your Applications, Places, System menu and select Edit Menus. In the window that comes up, highlight xine under Sound & Video. Now click properties on the right. In the new window where it says Command: xine, change it to say>> Command: gksudo xine

---

### Post by senorian on 2010-02-06
Many thanks. That got rid of "pps".
But i seem unable to delete xine.
It disappeared when i clicked on "delete" but continued to play when I went to the url.
I changed my preference to rhythmbox but xine remained.
I restarted the computer-still xine.
Any suggestions
thanks

---

### Post by warfacegod on 2010-02-06
Did you cahnge the command to reflect your Preferred choice?

---

### Post by senorian on 2010-02-07
yes
system>preferences>preferred apps>rythmbox

As an alternative to changing from xine could you explain how to reduce the size of the window with the word xine across it and how to get a window showing the data about the music playing.
Thanks

---

