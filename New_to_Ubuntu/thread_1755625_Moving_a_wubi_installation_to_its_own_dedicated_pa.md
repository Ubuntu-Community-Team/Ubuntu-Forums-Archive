---
title: "Moving a wubi installation to its own dedicated partition"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-05-11
Anybody know of a way I can move my Ubuntu wubi installation to a partition on my hard drive? I already made the space for it.

any hints or tips anyone? Thanks!

---

### Post by seawolf167 on 2011-05-11
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by skyzthelimit230 on 2011-05-11
Ah, I saw that thread, but I'm not sure how to actually use it. I downloaded the .tar.gz file and extracted it....but where do I go to start actually inputting the commands? haha

Sorry, I'm a quite the noob to Linux still

---

### Post by seawolf167 on 2011-05-11
Download the "wubi-move.sh" file, and note where you save it. The default will probably be in the /Downloads folder.

Once you have the script downloaded, open a terminal (Applications -> Accessories -> Terminal) and input the commands listed in there.

Start by moving to the folder where the "wubi-move.sh" file exists by typing

```
cd ~/Downloads
```To make sure the file is in this folder (and not downloaded to another folder), type

```
ls
```and look for the file name.

If it downloaded somewhere else, simply *cd* to that directory instead

```
cd /path/to/download/location
```Once you are in the correct folder, you can move on with his instructions under the "Automated Migration" section

Note that you're partition you setup will probably not be /dev/sda5, you can find this out by typing

```
sudo fdisk -l
```

into the terminal to list your partitions and their designations, then simply replace /dev/sda5 with the correct entry

---

### Post by skyzthelimit230 on 2011-05-11
Oh thank you! You provided the clues I needed to get started. The script is moving wubi to the new partition as we speak :D

---

### Post by seawolf167 on 2011-05-11
Awesome, glad it worked

If you are interested in learning more of the basics, you can start reading [here]("http://ubuntuforums.org/showthread.php?t=801404").

---

### Post by skyzthelimit230 on 2011-05-11
OK, thank you. Will start perusing everything on that link:)

---

