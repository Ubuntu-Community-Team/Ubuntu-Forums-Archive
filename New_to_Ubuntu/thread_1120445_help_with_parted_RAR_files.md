---
title: "help with parted RAR files?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by pjones0404 on 2009-04-09
I downloaded some tutorials that are rar's listed as part 1-4. When i open each rar it looks exactly the same. What do i need to do to use these tutorials?

---

### Post by Gen2ly on 2009-04-09
Theres a command line utility called unrar.  Not sure the Ubuntu package for it but I'm pretty sure it supports parted rar files:

```
unrar x file.rar00
```

Or whatever they are called.

---

### Post by tgyorgyi on 2009-04-09
I think rar and unrar do not get installed by default (not sure though). In case the above command does not work, go to Synaptic package manager and search for the word "unrar" and mark for installation. 

Once installed, if you prefer a GUI solution, File roller will also be able to deal with the parted rar file, just double-click on the rar file with the lowest number, and File roller should start.

---

### Post by binbash on 2009-04-09
you don't need to click or unrar e lower number, just select random one it does not matter

---

### Post by pjones0404 on 2009-04-09
Thanks for all the responses.

I am able to double click on the .rar files and open them with out issue. I am just curious as to why there are 4 different .rar files and when i open them they are all the same. I can extract the video tutorials and they play but i have not had a chance to go through the whole video to see if it cuts off in the middle or not. 

maybe i am over thinking the issue.

---

### Post by pjones0404 on 2009-04-12
bump....


any other explanations as to why there are numerous RAR files would be appreciated. Like i said i can open them but i am not sure if it is the while file as they are over an hour long each and i have not had time to tell if they are complete or not.

thanks again.

---

### Post by howefield on 2009-04-12
Quite often, large files are split into several "parts" to make them easier to upload or send, eg if you have a rapidshare account for file storage, the maximum file size you could upload was 100 meg (might now be 200meg) but either way, if you had a file of several hundred megabytes the only way to upload it would be to split it.

Some email accounts have limits on attachment size, one way to get round them is to split files that you want to send which are bigger than the limitation.

So on, and so on.,

---

### Post by pjones0404 on 2009-04-12
thanks for the response. I understand why they would be in parts based on upload and storage size limitations. 

what i do not understand is why they are all the same when i open them? If this is the case why do i need to download all of them?

thanks again.

---

### Post by TBerk on 2009-04-13
One answer would be that the utility you are using to open them is automatically stitching the various parts together so it appears that they are all the same when what you are getting is "start at the top page of the whole archive no matter which segment you double click on..." type behaviour.

 
TBerk
wow, one whole sentence...

---

### Post by nwadams on 2009-04-13
yes, just right click on one of them and hit extract here and it will extract them all into one file. Its a semi-obsolete method of sharing large files. howefield's answer is a good one too.

---

