---
title: "nautilus-script not running"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by ibig on 2010-01-02
Hi there.

I have followed the guide found here: [https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)
But it is not working.

I run Ubuntu Karmic 9.10. Have done the chmod on both the copyto and moveto file. I have also done the open scripts folder, logged in and out of my Ubuntu user session. Nothing does the trick so I'm hopping that one of you on this forum can help me.
It would be really great if we could get this to work.

Thank you.

Regards IBIG.

---

### Post by PhrankDaChickenGeek on 2010-01-02
Make sure you visit the Script folder with Nautilus - Open Nautilus, click the button next to the address bar, and enter /home/YOURUSERNAME/.gnome2/nautilus-scripts

The scripts are available when you right-click on a file or folder - Under "Scripts ->"

A quick walk-through: [http://www.youtube.com/watch?v=UQ6SBwruYVE](http://www.youtube.com/watch?v=UQ6SBwruYVE)

---

### Post by ibig on 2010-01-03
First of. Thank you PhrankDaChickenGeek for replying. I have already done the steps you suggest. That does not do the trick. Can you come up with other suggestions?

Thank you very much.

---

### Post by VCoolio on 2010-01-03
Do you have zenity installed?

---

### Post by Morbius1 on 2010-01-03
Did you make it executable?

chmod +x /home/username/.gnome2/nautilus-scripts/whatever

---

### Post by mechro on 2010-01-03
I don't know much about scripting but I think that Howto assumes you already know about starting a bash script with "#!/bin/bash".

For an introduction to Nautilus scripts you'll probably be better off looking here...

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

+1 for VCoolio's suggestion about zenity.

---

### Post by ibig on 2010-01-04
What solved was mechro's suggestion. I needed to specify #!bin Bash thing in the .sh script. So mechro was right the how-to guide obviously assumes that you know that. A little weird. I thought a how-to guide would show you excatly that, how to do something entirely not just 90%.
 
But thank you very much all of you.

---

