---
title: "Presario CQ62 sound problem with 10.4 - SOLUTION"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by KhanTG on 2010-09-28
I am making this post to provide a simple solution that worked for me on this machine.

**Symptoms:** sound worked for headphones but not for on-board speakers.

**solution:** open a terminal and type-> sudo nautilus
          navigate to File System and search for "alsa-base.conf"
          open "alsa-base.conf" in gedit and go to the bottom of the text
          put in the following lines and save the file--

              options snd slots=snd-hda-intel
              options snd-hda-intel model=hp-m4
              alias snd-card-0 snd-hda-intel
              options snd-hda-intel enable_msi=1

          reboot


after alot of searching on the forums I was able to find this information... but it took some searching and following references and doing the wrong thing once or twice.  this is what worked for me, and I didn't have to install a darned thing.

here's the original post that i got this info from: [http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667](http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667)

hope this helps someone.

---

