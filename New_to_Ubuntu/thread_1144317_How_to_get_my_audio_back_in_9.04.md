---
title: "How to get my audio back in 9.04?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Moondoggy on 2009-04-30
I'm looking for some help in regard to getting my audio fixed in version 9.04.

When I installed Ubuntu 8.10 everything worked flawlessly but I have tried to install the last two Ubuntu releases and each time I do I'm left without any audio.

I'm running an older Compaq EN550 and and in Ubuntu 8.10 it says that I'm running an ESS Audio Driver ES1869 and it also indiates that I'm running this under ALSA.

When I load up 9.10 the Volume control simply says that I have nothing configured.

So....  In newbie language, what exactly do I need to do to get ALSA installed and configured to use the ES1869 audio card I have in my system?

---

### Post by Didius Falco on 2009-04-30
Follow this guide for very comprehensive step-by-step troubleshooting and fixing:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+stops+working) 

I hope this helps!!

---

### Post by Moondoggy on 2009-04-30
Didius,

Thanks for the reply.

I followed the "Jaunty 9.04" instructions from the link you sent me and although PulseAudio appeared to be properly setup and working I still had no sound.  

Ran the troubleshooting Appendix A and when I ran "splay -l" in the terminal it said I had no driver.

Found another article [https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards) and as soon as I ran "sudo modprobe snd-es18xx" in the terminal I had audio. 

Followed the instructions and added "snd-es18xx" to /etc/modules so that it would be loaded at boot time.

Restarted the machine and I still had audio so my problem is now resolved.

I hope that with the link you provided plus what I found in the the other article someone else may also solve their audio problems as there was a long list of drivers in the second article (like snd-sb16 for SoundBlaster 16) and the fix was pretty simply once you had "how to" instructions.

---

### Post by Didius Falco on 2009-04-30
I'm glad you got it working. And thanks for linking the other guide that helped you. If you would, please mark this thread as solved, so that others with the same problem will see that it resolved yours.

To do so, edit your first post, and when the edit screen comes up, click the **Go Advanced** button.

This will take you to an editing screen that will let you change the title of the thread. Simply click on the end of the title and start typing "solved" and it'll give you some choices on how to phrase it.

As long as you are there, You might think about making the thread title more descriptive - something along the lines of  [B]ES1869 audio card no sound in 9.04 solved.
[/B]
That way any other ES1869 card owners have a better chance of finding it with a search.

Enjoy your music!

---

