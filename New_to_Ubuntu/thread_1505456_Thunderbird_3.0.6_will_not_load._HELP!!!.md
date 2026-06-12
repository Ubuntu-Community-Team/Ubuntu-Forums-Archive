---
title: "Thunderbird 3.0.6 will not load. HELP!!!"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by seanbw on 2010-06-09
I normally use Ubuntuzilla to install Ubuntu but I somehow lost the plot and downloaded Thunderbird 3.0.4 whilst Synaptic asked me to upgrade to Thunderbird-3.0.6.
After installing both Thunderbird 3.0.4 (to opt/thunderbird) and 3.0.6 to whereever Synaptic installed it to, I realised my mistake and deleted /opt/thunderbird-3.0.4/ and following the advice in [http://www.kabatology.com/07/29/a-single-command-install-of-thunderbird-3-beta-3-on-ubuntu/](http://www.kabatology.com/07/29/a-single-command-install-of-thunderbird-3-beta-3-on-ubuntu/) amended the profile at /home/seanbw/.thunderbird-3.0 to point to /home/seanbw/thunderbird-3.0.
Now when I load thunderbird, I get this error message:

> Thunderbird-3.0 is already running, but is not responding. To open a new window, you must first close the existing Thunderbird-3.0 process, or restart your system

I have checked the system monitor and there is no thunderbird running. I have restarted Ubuntu to come back to same error message.
My problem is how do I transfer my current profile currently at /home/seanbw/.thunderbird-3.0.3 to my current profile at /usr/lib/thunderbird-3.0.6pre/thunderbird

My Synaptic shows I have two versions installed. version 3.0.3 and 3.0.6 and both wont run.
I can't afford to lose my current profile as it contains a lot of emails and activity. How can I transfer my profile and stop this error message?

---

### Post by seanbw on 2010-06-09
These are the files installed by Synaptic for Thunderbird-3.0.6:
> /.

/usr
/usr/bin
/usr/bin/thunderbird
/usr/lib
/usr/lib/thunderbird-3.0.6pre/thunderbird
/usr/lib/thunderbird-3.0.6pre/thunderbird-bin
/usr/lib/thunderbird-3.0.6pre/thunderbird.sh
/usr/share/pixmaps
/usr/share/pixmaps/thunderbird.png

---

### Post by seanbw on 2010-06-09
I tried to run from the terminal but all I got were:
```
root@acer-laptop:/usr/lib/thunderbird-3.0.6pre# ./thunderbird.sh
No protocol specified
No protocol specified
Error: cannot open display: :0.0
```
Any help?

---

### Post by seanbw on 2010-06-09
bump

---

