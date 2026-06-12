---
title: "xfce xkb plugin doesn't remember the settings between sessions"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by netimen on 2011-08-01
I'm running xubuntu 11.4 on a Lenovo T520 laptop. 

I have two keyboard layouts installed and I use the xfce4-xkb-plugin to display the current layout indicator and to set the switching between layouts hotkey.

The problem is that when I restart my computer, the xkb plugin resets all the settings to default, so I have to set them every time my system starts. Can I make it remember the settings (the layout switching hotkey, and the Compose key)?

---

### Post by cipricus on 2012-01-22
I have the same issue, I add 3 or 4 different key layouts  but after I restart I am left with the main one.

I am talking about xfce4-xkb-plugin in xUBUNTU 11.10

---

### Post by cipricus on 2012-02-27
I think I got a solution -  - which works after many reboots!

What I found (by accident) is that upon restart the xfce4-xkb-plugin settings that were loaded were those from the file '/home/user/.config/xfce4/xfconf/xfce-perchannel-xml/keyboard-layout.xml'

Those from '/home/user/.config/xfce4/panel/xkb-plugin-43.rc' are settings configured by user in Keyboard Layouts properties, but they are not saved after reboot. I do not know exactly why, but I think that any contradiction between these two files makes the customization to be reset to the data in the xml file.

My solution - is the following:

[B]- edit your settings in Settings Manger/Keyboard/Layout (I use Xubuntu) and in the xfce-xkb-plugin settings and make sure they are _the same_.
- edit the file '/home/user/.config/xfce4/xfconf/xfce-perchannel-xml/keyboard-layout.xml'  with _the same_ options[/B] (check the rc file too)

contents of this file should be something like** [this]("http://pastebin.com/FgGtY3a2")** - where the languages are: Romanian standard version, US and French
while contents of the rc file mentioned are like** [this]("http://pastebin.com/NLXNvwf4")**
look in the rc file and modify your xml file accordingly (I mean in my case I put the 'std' part where it should)
the 'alt_caps_toggle' (in my case) is only in the rc file but will be remembered if _**all the rest**_ of the data are the same in the xml.

---

### Post by dlazerka on 2012-10-20
Thank you, cipricus!

---

### Post by cmcanulty on 2012-10-20
I also want to do this but can't find anything to open an xml file. I installed XML Copy editor but it won't open.

---

