---
title: "Have thumbnails,but where are the actual files? Help please!"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by John Macnab on 2010-09-05
Hi everyone
           I would like to have a newbie question answered,and if I need to elaborate on anything, please tell me and I will. I have an old hdd that is from my old computer lying about and yesterday I connected it to my current machine and re installed grub on it-btw it has Windows XP and Ubuntu (Gutsy Gibbon).I managed to log into Ubuntu but I remembered that I had some pics and vids in a folder in that hdd and tried to find it but it seems to have disappeared. I even tried enabling 'show hidden files and folders' but to no avail. But,in a hidden folder named thumbnails, I found thumbnails of the pics and vids I was looking for. They had weird long names (hexadecimal I think),and have the extension .png- But where are the actual files themselves? Is it possible that when I was upgrading my computer, I had myself deleted that folder and the thumbnails remained due to some strange reason? Or does the very presence of those thumbnails indicate that the original files are indeed still on the hdd? (If so, how can I find them?). I have tried going into all the different folders in both my Ubuntu and XP partitions, but the real files are proving elusive. If somebody out there can clarify my doubt,please do post here.I would be very thankful for any replies that come this way,this thing is driving me nuts hehe.Thank you for reading this rather long question.

---

### Post by Elfy on 2010-09-05
If you think they are jpg's you could try 

```
sudo find / -type f -iname "*.jpg" -print
```

You could change the / to ~/ for instance to search in your home folder

Edit obviously you could change the type as well ;)

---

### Post by John Macnab on 2010-09-06
Sir/Madam, ty very much for giving me that code. I tried different kinds of files like *.gif,*.jpg etc but it didnt return the files that I was looking for. I didnt change the '/' to '~/',I just typed the same thing as you posted which I suppose looks up at all drives and folders? Sorry I am not very computer savvy :( I didnt find any reference to the files that are missing so I suppose that means the original files are no longer on the hdd? In which case,why is it showing previews of the files in the thumbnails folder? I guess that is simply the way Ubuntu works?*Quite confused about it but then I am a newbie who lacks computer knowledge* Anyhow,thank you so much for giving me that code :)

---

### Post by col48 on 2010-09-06
I think the presence of the thumbnails does not imply the originals are still there.  You could try navigating to the thumbnails folder in your file browser (eg nautilus) and right-clicking it.  A menu should come up including 'Properties'.  Click on that.  It might tell you something useful, although I rather think it will not get you very far.  It should tell you when the thumbnail was created which just might give a clue.

---

### Post by John Macnab on 2010-09-07
Ty for replying, sir/madam,I guess you are right when you said that just the presence of the thumbnails doesnt indicate that the originals are still there. I tried looking at the properties but it didnt say anything useful. Oh well I guess I might as well format the hdd. But thanks you very much for posting,atleast now I know that the thumbnails need not be a sign of the presence of the original files hehe.

---

