---
title: "evolution can't store folder"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by duruttye on 2009-05-20
Hey there!

I use evolution for a while now, and I'm experiencing some problems regarding the storage of my sent folder. Although I have exactly 74 sent messages in this folder, the file of the folder is more then 2 GB!!

Anytime I shut it down, it takes ages to store the folder, meanwhile the laptop is unusable. Sometimes it shows that it can't send the message, but it was already sent :)
I know I don't have any big attachments, although I can't add columns like size of the message.

Any ideas?

Using ubuntu 9.04, on a dell vostro, 3 gb ram, 2.2 mhz dual core processor and 10 gb free space on the /home partition.

thank you!

---

### Post by camper365 on 2009-05-20
If you run```


cd ~
cd .evolution
cd mail
cd local
gedit Sent
```You will be able to view the HTML of the messages and you can also use ```
ls -gh
``` to view the size of the Sent file
> 
Using ubuntu 9.04, on a dell vostro, 3 gb ram, 2.2 **mhz** dual core processor and 10 gb free space on the /home partition

I think you might mean ghz, not mhz (2.2 mhz is slower than a very slow calculator) :)

---

### Post by duruttye on 2009-05-20
This is the size:

[HTML]2.0G 2009-05-20 22:14 Sent[/HTML]

and yes, I meant GHZ :)

Now evolution will start in about 10 minutes and in that time the laptop is unusable, I have 74 messages in there, isn't that strange? In the inbox there are a few thousand messages and it isn't by far that big the Inbox file in the /local folder.

Gedit won't open it in a few minutes, and if it would, I haven't a clue what to do next :)

---

### Post by camper365 on 2009-05-20
I have 43 messages in the sent folder and mine is only 600K, so yes 2G is very big.

---

### Post by mprince on 2009-05-20
You could open the sent text file and take a look at it.

You could try editing it and remove any unnecessary entries. 

Look at the first message in your sent box (the oldest) then delete everything before that in /.evolution/mail/local/Sent

Back up the /.evolution folder just in case you encounter problems.

---

### Post by duruttye on 2009-05-21
Whenever I tried to open that file (2GB!!) with gedit or nano, ubuntu will log out and in my user, in dmesg I saw something like: out of memory :)

---

### Post by mprince on 2009-05-21
OK, try this.

Open Evolution... Select the Sent folder so you are viewing it.

Then from the menu choose *Folder>Expunge*.

---

### Post by duruttye on 2009-05-21
wooaaa, that was it!!!

now its down to 20 MB!!!

thank you very much!!!

---

### Post by mprince on 2009-05-21
Glad that worked for you duruttye. :p

---

