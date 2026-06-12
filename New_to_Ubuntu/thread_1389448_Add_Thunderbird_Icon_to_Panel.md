---
title: "Add Thunderbird Icon to Panel"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Sky Aisling on 2010-01-24
Here's the goal: I would like to add Mozilla Thunderbird Mail Client icon to the xfce panel then be able to launch the program from clicking the icon.  Is this possible?

Currently Mozilla Firefox icon is resident in the panel and works perfectly.

How do I add the Thunderbird icon next to it and have it launch like Firefox?

I've read the xfce manual comments about adding 'launcher' but am not quite understanding this yet.  Thanks for your patience.

---

### Post by Rex Bouwense on 2010-01-24
> **Sky Aisling said:**
> Here's the goal: I would like to add Mozilla Thunderbird Mail Client icon to the xfce panel then be able to launch the program from clicking the icon.  Is this possible?

Currently Mozilla Firefox icon is resident in the panel and works perfectly.

How do I add the Thunderbird icon next to it and have it launch like Firefox?

I've read the xfce manual comments about adding 'launcher' but am not quite understanding this yet.  Thanks for your patience.


I believe that all you have to do is right click the panel then > + Add to Panel > Application Launcher > Forward > Internet > Thunderbird > Add.  That should do it for you.

---

### Post by herbertportillo on 2010-01-24
If you already have Thunderbird installed on your computer, I'm guessing you go to "Applications" and open it that way. If that's how you open Thunderbird, I'm pretty sure you can just drag the Thunderbird icon from the menu to the panel and add it that way. I don't use Xubuntu, I use Ubuntu. But I'd be amazed if XFCE couldn't do that.

---

### Post by 73ckn797 on 2010-01-24
If T'bird shows in the Applications menu you may only have to right click and select add to panel. Similar to what was already mentioned.

---

### Post by Sky Aisling on 2010-01-24
Thank you, Rex for the quick reply! I will try the suggestion.

---

### Post by Sky Aisling on 2010-01-24
Thank you all for the quick reply! I will try the suggestions.
Here's the situation so far:
Yes, Thunderbird is resident on my Xubuntu system.  I am currently running it as 'Thunderbird.desktop' with a shortcut link on the desktop screen.  It is listed in my /home directory as 'Thunderbird.desktop'. Also, it is listed in Applications/Network/Mozilla Thunderbird... I can also find it using 'Application Finder' and by searching with 'Catfish'.  Catfish gives me many location references to Thunderbird.

In attempting to get Tbird icon to show in XFCE panel, I have right clicked the icon in all of the above screens (except Catfish locations) and drug the icon to XFCE panel.  In none of the attempts can I get the icon to transfer to the panel.  Perhaps I can go to the locations that Catfish shows and drag an application from there?

The 'launcher' icon successfully transfers to the panel but it seems to be empty.  

Rex, I've tried your suggestion "right click the panel then > + Add to Panel > Application Launcher > Forward > Internet > Thunderbird > Add."  I'm stuck on the 'forward'.  What do you mean by 'forward'?

---

### Post by Sky Aisling on 2010-01-24
Sweet Success!  Here is what I did to get the Thunderbird icon to show in XFCE panel and to launch the application:

I set the Launcher' app into the XFCE panel by right clicking the panel and choosing 'Launcher' to add to the panel.
then...
I went to system/user/share/applications (I found this location through a 'Catfish' search for 'Thunderbird') and located the Thunderbird icon.
I drug the Tbird icon from system/user/share/applications to the open 'Launcher' app window. 
Walla! the Tbird icon transferred all its data to the Launcher window and now the Tbird icon shows in the panel and correctly opens Thunderbird Mail. 
Thank you everyone for the help.

---

### Post by Sky Aisling on 2010-01-24
PS  How do I close this thread?

---

### Post by 73ckn797 on 2010-01-24
> **Sky Aisling said:**
> PS  How do I close this thread?
Thread tools and mark as "Solved".

---

