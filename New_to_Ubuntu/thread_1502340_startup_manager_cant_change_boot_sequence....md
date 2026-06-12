---
title: "startup manager cant change boot sequence..."
date: 2010-06-05
forum: New to Ubuntu
---

### Post by mustard greens on 2010-06-05
I have two separate OS partitions, but grub automatically selects the wrong one.

I tried through startup manager to change the default selection, but no change during next boot.

I have un-installed/reinstalled startup manager, no change.

I have also looked for bug reports, none found.

I am aware of tutorials on how to do this manually through CLI, but was wondering if I should submit a bug report (never done it.  will have to learn how)

for clarity, the start up manager list and grub2's list of available OSs are in a different order with different titles, but I am sure of the selection I am trying to make and which is which.

any suggestions?

---

### Post by drs305 on 2010-06-05
For just setting the default OS, you can use this guide:
```

```[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

However, if you are still trying to figure out why StartUp-Manager doesn't select the correct OS the above guide won't help. You could post the results of running this script and we could take a look at your system's boot process:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

As far as submitting a bug report, it's now pretty easy by running the command
```

ubuntu-bug startupmanager

```
I would wait and see what develops in this thread before submitting it though. SUM was designed to work with Grub legacy, and parts of it (including determining the default OS) should work with Grub2. I haven't seen problems with it in this regard, but the app certainly isn't as 'robust' with G2 as it was with Grub legacy.

---

### Post by barney385 on 2010-06-05
You didn't specify which OS's you're using.

This may be helpful: [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

---

### Post by mustard greens on 2010-06-05
ok, so this gets more strange.  I edited and saved with gedit /etc/default/grub.  I set the default to the correct number (remembering that the first position is 0) and still grub offers the SAME wrong selection as the default offering???

---

### Post by mustard greens on 2010-06-05
@barney385

it shouldnt matter which OS I am using, but I am using 10.04, which is listed in my signature.

---

### Post by mustard greens on 2010-06-06
@ drs035

not sure how to run the script you linked to.  as per my other post CLI changes are not taking effect either.

---

### Post by drs305 on 2010-06-06
> **mustard greens said:**
> not sure how to run the script you linked to.  as per my other post CLI changes are not taking effect either.

The instructions on how to run meierfra's boot info script are located on the linked page. The script should download to your Desktop or the Downloads folder (or whatever you have set as a default).

Run this command:
```
sudo bash [path/to/the/download_folder]/boot_info_script*.sh
```

The RESULTS.txt should be in the same folder as the downloaded script.

More information on the linked page ( [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by mustard greens on 2010-06-06
here is the txt document as requested.  sorry, not always so bright with the CLI stuff. not sure if my attachment of said file was successful.  the file seemed too big to copy/paste.

thanks for sticking around to help.

---

### Post by drs305 on 2010-06-06
You appear to have the Grub2 files installed in two locations - once on sda1 and again on sda3. The reason for your troubles is that you are running Lucid from the sda1 partition but the Grub you are using is installed on sda3.

First, make sure after you boot that you are really running Lucid from sda1:
```
mount
```
You should see /dev/sda1 mounted on /

Next, install grub-pc on sda (note that no partition is designated). This should write Grub2 to the MBR and write the files to sda1's /boot/grub folder. More importantly (since the files are actually already there), it will tell your system that the Grub2 files are located in the sda1 partition.
```
sudo grub-install /dev/sda
```

Update grub with the following, and on rebooting you should be using the sda1 Grub files:
```
sudo update-grub
```

---

### Post by mustard greens on 2010-06-06
worked like a charm!

so how did I end up with grub working off of sda3?

I created the separate partitions using GParted, and then filled them using the GUI installation from the Live CD.

as far as I remember I chose "/boot" for sda1, and "/" for sda3.

does this sound correct?

of course I dont expect you to deduce how I messed things up, but would those not be the correct designations if I wanted to boot from sda1 and not sda3.

thanks anyway for getting me back to normal.

---

### Post by drs305 on 2010-06-06
> **mustard greens said:**
> worked like a charm!

so how did I end up with grub working off of sda3?

From what I can see, the entire OS was installed on sda1 rather than just /boot. It's possible your inadvertently selected / rather than /boot. It might be that if Ubuntu was already installed on sda1 perhaps you didn't choose to format the partition although I can't say for sure what would happen in that case.

Assuming you are now using sda1, you might look at the contents of sda3 and then reconsider it's label - "OS2".

In any case, glad you got things working again.  :-)

---

