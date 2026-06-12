---
title: "Can't empty .Trash-1000 from smarphone..."
date: 2010-11-22
forum: New to Ubuntu
---

### Post by 3tz3r on 2010-11-22
Yesterday I plugged in my smartphone into my desktop running Ubuntu 10.10 and deleted approx. 1.2GB of files from it. I assumed it all went well, but when I disconnect the phone it shows no difference in the total space available/used. I Googled and found out about the .Trash-1000 folder so I pressed Ctrl+h and there it was, all 1.2GB was in that folder so I deleted it. However, it still shows the same amount of space available/used. I don't want to have to format the phone since I'll lose my data; all my apps will have to be reinstalled, I'll have to re-sync 4+ GB of music, etc. Any idea what I could do?

---

### Post by yankysunny on 2010-11-22
try to do it from terminal.
```
rm -f {path of that trash folder}
```

---

### Post by 3tz3r on 2010-11-22
Thanks, but my problem is that I deleted the trash folder, but the phone still shows no change in space available/used. The only difference is that now I can't see the folder...

---

### Post by yankysunny on 2010-11-22
I am amazed that Ubuntu allowed u to do so!!
do ctrl+h if any other folder has the contents like trash?

---

### Post by 3tz3r on 2010-11-22
> **yankysunny said:**
> I am amazed that Ubuntu allowed u to do so!!
do ctrl+h if any other folder has the contents like trash?
OK, I put a text file into the phone and deleted it, then pressed ctrl+h and there's a new .Trash-1000 folder. However, the 1.2GB of content is not there, just a couple of KB from the text file...

---

### Post by igotsanevo4g on 2010-11-22
I take it you have an android phone, because this happened to me.

I deleted some random stuff, and i go into the sd card and theres this wierd trash file with all my junk in it. So i just deleted it with my file manager app. (astro)

I dont understand what other problem youre describing, try unmounting and remounting the SD?

---

### Post by 3tz3r on 2010-11-22
> **igotsanevo4g said:**
> I take it you have an android phone, because this happened to me.

I deleted some random stuff, and i go into the sd card and theres this wierd trash file with all my junk in it. So i just deleted it with my file manager app. (astro)

I dont understand what other problem youre describing, try unmounting and remounting the SD?
Actually, I have a [Meizu M8SE with 8GB of internal storage]("http://meizu.com/") and it runs a customized version of Windows CE6.0. And, yeah, I also tried deleting the new .Trash-1000 folder with the file manager and but that didn't solve my problem either.

---

### Post by igotsanevo4g on 2010-11-22
> **3tz3r said:**
> Actually, I have a [Meizu M8SE with 8GB of internal storage]("http://meizu.com/") and it runs a customized version of Windows CE6.0. And, yeah, I also tried deleting the new .Trash-1000 folder with the file manager and but that didn't solve my problem either.

So if you go in there with your file manager, and delete it. Then check your storage amount, it says that its still there?

Try deleting it while mounted to a windows pc or re-try with ubuntu.

Have you turned it off since trying the delete it?

---

### Post by 3tz3r on 2010-11-22
> **igotsanevo4g said:**
> So if you go in there with your file manager, and delete it. Then check your storage amount, it says that its still there?

Try deleting it while mounted to a windows pc or re-try with ubuntu.

Have you turned it off since trying the delete it?
Yes, when I check the available storage space it's still the same. I restarted the phone and still, no difference. I don't have a PC with Windows, though... :sad:

---

### Post by igotsanevo4g on 2010-11-22
> **3tz3r said:**
> Yes, when I check the available storage space it's still the same. I restarted the phone and still, no difference. I don't have a PC with Windows, though... :sad:

Try cutting it out of your phone to your PC, instead of trashing it.

---

### Post by koleoptero on 2010-11-23
You can also just copy all your files on your PC, then format the card, and then copy them back.

---

### Post by 3tz3r on 2010-11-24
> **koleoptero said:**
> You can also just copy all your files on your PC, then format the card, and then copy them back.
That's exactly what I was trying to avoid, but I ended up doing it anyway. I formatted the phone and synced my stuff onto it again and the lost storage space was back. Luckily, my phone has a backup option that prevented me from losing my apps and having to install them all again.
 
Ubuntu is a great operating system, but seriously, have some common sense! How are new users supposed to know that they can't actually delete something from their USB device without clicking shift+del, or that they have to go to File->Emtpy Trash before disconecting their device?

---

### Post by Yougo on 2010-11-24
to my knowledge, deleting the trash folder should just delete it, and everything in it. why that space wasn't set free again, i don't get either.

normally when you right-click a removable drive, and choose disconnect/unmount (not sure, non-english box here) ubuntu should ask you to empty the trash on that volume automatically.
just yanking it out causes the trash folder to stay full.

---

