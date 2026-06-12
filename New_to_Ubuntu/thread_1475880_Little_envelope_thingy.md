---
title: "Little envelope thingy"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by fatphilthethird on 2010-05-07
Such a noob question; what's the little envelope thingy on the top panel called? The one that links to email, IM etc?

I wanted to search for a way to get it to refer to thunderbird rather than evolution but realised I didn't know what it was called...

---

### Post by natravis on 2010-05-07
[http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/](http://www.kabatology.com/03/27/how-to-change-your-default-applications-mail-client-in-a-gnome-desktop/)

Seems to be what you need, though the menus have changed slightly.

---

### Post by KdotJ on 2010-05-07
I'm not sure its posible to point this to thunderbird. I may be wrong however...

I actually switched to using evolution because of this little envolope and switched to using empathy instead of emesene for my instant messenger. Try them a try, you might like evolution. However if you're not impressed, maybe some one will be able to help you with getting thunderbird to the icon. Sorry that I can't help more.

---

### Post by plucky on 2010-05-07
> **fatphilthethird said:**
> Such a noob question; what's the little envelope thingy on the top panel called? The one that links to email, IM etc?

Right click on icon and select **About**= Indicator Applet

---

### Post by fatphilthethird on 2010-05-07
Thanks **plucky**!

Have tried evolution before **KdotJ** and don't really like it, plus it doesn't support imap idle as far as I can see. Also don't like the way it handles deleting emails in my gmail account.

Have set the default email ap to thunderbid **natravis**, but the notification applet still launches evolution.

---

### Post by Georgia boy on 2010-05-07
Whenever I click on the envelope I also get Evolution opening. I clicked on the about also and nothing happened. I always go to the applications to open Thunderbird and with it open Evolution still opens when I click on the envelope. Is it set up for Evolution only and blocks anything else?

Thanks

Tom

---

### Post by empty_spaces on 2010-05-07
I can't launch thunderbird via the envelope, but during my search for a tray notification icon for Thunderbird, I was actually able to integrate all the thunderbird notifications to be displayed via the envelope.

If that is something you want to do, check out all my posts in this thread.
[http://ubuntuforums.org/showthread.php?t=1465709](http://ubuntuforums.org/showthread.php?t=1465709)

---

### Post by natravis on 2010-05-07
[http://ubublogger.wordpress.com/2009/12/11/experimental-indicator-applet-support-for-thunderbird-finally-available/](http://ubublogger.wordpress.com/2009/12/11/experimental-indicator-applet-support-for-thunderbird-finally-available/)

Check it.

---

### Post by Vined Adobo on 2010-05-07
> **fatphilthethird said:**
> Such a noob question; what's the little envelope thingy on the top panel called? The one that links to email, IM etc?

I wanted to search for a way to get it to refer to thunderbird rather than evolution but realised I didn't know what it was called...


Right click on indicator applet envelope.  Click on about.  Click on link to Indicator applet website.  This will open a page in Firefox.  Click on Answers and search for thunderbird.  Follow resulting directions. 
 
# [by]Rodrigo Donado  said on 2009-12-02:
#
# To launch Thunderbird from the Indicator Applet:
# Create a file named ‘thunderbird’ in:
# /usr/share/indicators/messages/applications/ folder with the following contents:
# ‘/usr/share/applications/thunderbird.desktop’.


 Now, I'm not sure how to place text into a folderI suspect it's a link and I still have to fret about those.  Someone here can halp you with that, though.

Hope this helps
Dave

---

### Post by dracayr on 2010-05-07
not a link, just create a new text file in the directory /usr/share/indicators/messages/applications/, call it thunderbird, and let it have the contents '/usr/share/applications/thunderbird.desktop'. You'll need root rights to do that.
In the CLI:```
gksudo gedit /usr/share/indicators/messages/applications/thunderbird
```(for gnome users) and copy-paste '/usr/share/applications/thunderbird.desktop', save.

dracayr

---

