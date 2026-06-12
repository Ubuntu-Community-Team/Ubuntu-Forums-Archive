---
title: "can ubuntu PCs join WIn7 Homegroup?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by sallam on 2010-10-02
Greetings

I would like to join a homegroup with other PCs at home. The other PCs run WIn7.
Can my ubuntu laptop connect and share files and stuff with other computers in a Win7 Homegroup?
If so, please give me the steps to do so.

Many thanks.

---

### Post by Troublegum on 2010-10-02
Yes, of course. 
If you want to connect your ubuntu to windows shares, have a look at the program "pyneighboorhood". You can install it via
```
sudo apt-get install smbfs pyneighborhood
```
After that, you can navigate to *Applications* -> *Internet* -> *pyNeighborhood*. This programm will search your network for other PCs and available shares. You can connect to them with a few clicks. 


If you want to share files from your ubuntu laptop with others, you can install samba:
```
sudo apt-get install samba
```
Open up nautilus (the file manager) and navigate to the folder you want to share. Do a right-click on that folder and select the share option (don't know the exact name right now). There should now be a small window where you can enter the name of the share, select if the share is writeable for others and if guests can connect to it. 

After that, you'll see a new icon with two arrays right to a shared folder:
[img]http://img299.imageshack.us/img299/3352/imagetargetsambaserverg.png[/img]

---

### Post by sallam on 2010-10-02
I folowed your instructions. The samba part worked and the 2 arrows showed up on the folder. But I failed to figure out how to use pyneighborhood. I see the other computer's name listed. But what do I do next? clicking it result in nothing, right-clicking it has no outcome either.

---

