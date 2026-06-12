---
title: "Instillation Problems"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by artoo36 on 2009-01-19
Hey all!

Sorry to bother you again so soon after my last question, but I have searched around on Google and in other forums and have had no luck in finding an answer.

I have been following the instructions for setting up a dual boot located at this site:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)


However, when I get to the last step, the migration assistant does not list "Windows Vista/Longhorn (loader)".

I also get the following message below that:
"Warning: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.
The following partitions are going to be formatted:
partition #5 of SCS13 (0,0,0) (sda) as ext3
partition #6 of SCS13 (0,0,0) (sda) as swap"

In my research, I found that roughly a third of the people who encountered this went ahead and installed anyway and everything worked just fine, roughly another third had their Vista install wiped, and the remainder were unsure of whether or not to try. I am currently one of the remainder... 

Anyone have any thoughts?

Thanks!

---

### Post by mrbiggbrain on 2009-01-19
when the install asks you if you want to install, on the whole disk, reformat linux patririons, or custom, you cna choose custom and just make a directory that you know is ok / 

doing this wrong will render your vista install "screwed" just please dont tell the installer to use the whole disk.

---

### Post by yeats on 2009-01-19
First of all, do not "just do it" if you're not sure about what you're doing.  I know it's exciting, but *resist the temptation*! :-)

When you get to the point where the installer says "Prepare Disk Space" and you have selected to install in the largest continuous free space, the installer will NOT overwrite anything.  Assuming you have followed the advice about shrinking the Vista partition, all should go well.

Good luck, and let us know how it goes!

:-)

---

### Post by mrbiggbrain on 2009-01-19
if you have an externel HDD you can actualy make a hard backup of your partition useing Gparted.

just copy the partition to the new drive, and let it go (mkight take quite a while) then if something goes, OWIE, you can delete the old, and copy over the new.

its the method i use to transfer old HDD to new ones at work (im an easy tech) it works on windows partitons fairly well.

---

### Post by artoo36 on 2009-01-19
I do not yet have an external, though I am in the market for one, once I earn a little bit more.
As much as I wish otherwise, I don't have the cash to buy all the tech-toys I'd like.  :p

I guess I could go ahead and try the install. I did shrink the vista partition, and I am using the "largest continuous space" option.
I also just made a restore disk set, so I have back up...

I just get nervous about messing stuff up. I know enough to get myself into trouble, but rarely do I know enough to get myself back out again. :)

---

### Post by artoo36 on 2009-01-19
Success!!! Ha!

You guys are awesome. I much prefer you to Microsoft. :D

---

