---
title: "help with nm-applet and WPA howto"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by pmdkh on 2007-10-05
I am trying to configure WPA in Edgy Eft, using the [_WPA Howto_]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") and I ran into a little roadblock. The applet for Network Manager is not showing up. When I type in the command ```
nm-applet
``` nothing happens. The terminal doesn't display any error messages, but just sits there. I have to hit Ctrl+C to get out of it.

Would anyone happen to know why I can't get the applet running?

Thanks for your help.

---

### Post by pmdkh on 2007-10-06
Bump.

**Edit:** I figured out why it wasn't showing up, thanks to [_this thread_]("http://ubuntuforums.org/showthread.php?t=324877").

Now I have another problem. When I right click on the Network Manager applet, "Enable Networking" is already checked. However, when I try left-click on it, it says "No network connection". I don't understand why it says this, especially since I am currently on the Internet.

Does anyone have any idea?

---

### Post by pmdkh on 2007-10-06
I finally got everything working, after a little reading. The reason that Network Manager wasn't seeing any connections was because they were already configured. This [_documentation for Network Manager_]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28networkmanager%29") fixed my problem. (Funny how that works.)

---

