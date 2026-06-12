---
title: "Nautilus only crashes in home folder? can access via gksudo nautilus."
date: 2009-04-12
forum: New to Ubuntu
---

### Post by pjones0404 on 2009-04-12
I am having issues with nautilus. I am able to browse all other areas except my home folder. I am able to view the file system and other partitions but when i try to go to my home folder nautilus stops responding. I am not sure what could be causing this. It started when i was creating a folder and moving some pictures into it. 

i am able to access it via gksudo nautilus but not as my normal user. Any tips would be great. thanks.

---

### Post by aktiwers on 2009-04-12
Does it give you any error when you open it as normal user from terminal?

---

### Post by drs305 on 2009-04-12
This is a bit different than a reported bug. It could be trying to open the folder with the wrong app. Try opening nautilus, right click on any folder, and select "Open with other application". Choose "File Browser" and click "Open".

---

### Post by SKLP on 2009-04-12
I would try this:
Begin by closing any nautilus windows that are opened...
```
$ cd
$ rm -rf .nautilus
$ killall -9 nautilus

```

---

### Post by sgosnell on 2009-04-12
Or try using a terminal, and deleting the folder from there, then make a new one with Nautilus.

---

### Post by pjones0404 on 2009-04-12
nope. I type in nautilus and it opens a new window but it just goes to not responding. I attempted to run the command nautilus /home for example and it opens that directory no issue. If i click the icon for my user is stops responding. 

I notice that when i run the command that the terminal just goes to another prompt to enter a new command. Is there a way to leave the terminal command running so that when i navigate the the home folder i can see if it displays an error via terminal?

thanks for the quick response.

 - edit - 

i tried opening with a different application and selected file browser and it still crashes. SO i should delete the folder that i made when the issue started. It is just a fodler with like 4 pictures in it. I will try the other command suggested and BRB.

---

### Post by pjones0404 on 2009-04-12
ok i got it.

I ran the command rm-r foldername. Once the folder that i created previously was gone i was able to access my home folder via nautilus. I am no sure what happened but i appreciate the responses.

---

### Post by sgosnell on 2009-04-12
It was probably a corrupted file that Nautilus was trying to read.

---

