---
title: "Imported user data from 9.04 to 10 on install not there"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-06-30
OK I bit the bullet and jumped from Jaunty Jackelope to 10.04 LTS.
I installed 10.04 (from CD) alongside the existing  9.04 and Windows XP. just in case I needed to revert if 10 was a bust.

During the install it asked which accounts to import and I checked mine and my wife's. After the install I have no desktop data and my home folder is empty.

I have a 9.04 recent backup on another hard drive and I still have 9.04 as an OS choice on boot.

What would be the easiest way to restore my data to the Lucid Lynx install?

Thanks.

---

### Post by ubunterooster on 2010-06-30
Manually coping files from Jaunty seems to be the easiest way.

---

### Post by ozark_hillbilly on 2010-06-30
Which directories do I need to copy to get:

my personal data files including Desktop configuration
evolution data
configuration data (internet)  - Is this under /etc ?
downloads using synaptic pkg mgr

Ed

---

### Post by ubunterooster on 2010-07-01
You will want to copy the Documents, Downloads, Music, Pictures, Public, and Video folder from your old partition to your new one.

For installed programs, just use the "Save Markings" function in Synaptic on the original  install and the "Read Markings" function on the new install and point it to the "saved" file when it wants a location.

For firefox, go to the .mozilla folder in your old home, go to firefox subfolder and copy the folder with a random 8-digit file name into your new firefox folder. Then edit the "profiles.ini" file in the mozzila>firefox folder so the [COLOR=SeaGreen]Path[/COLOR]= reads the folder name of the one you copied from the old profile. 

Not sure about evolution or most other settings...

---

### Post by ozark_hillbilly on 2010-07-02
I am so confused!

I don't see a NEW partition for the Lucid install. My 250 gig drive still has 150 allocated for Linus and 50 gig for DOS.

I also cannot get file permissions to move files to the folders under Lucid. Should i be using nautilus or changing ownership of files somehow?

would it be better to boot under Jaunty and move the files to Lucid or vice versa?

File permisisons is giving me fits....

---

