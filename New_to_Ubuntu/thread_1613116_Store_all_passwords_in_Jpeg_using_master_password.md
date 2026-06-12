---
title: "Store all passwords in Jpeg using master password"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-04
I have many accounts and different passwords for each accounts.Its tough for me remember each and every password.In windows there is a software to store texts in any file,we can store our passwords or texts in mp3,jpeg,video or whatever file we want and we have to remember only master password..Is it possible to do it here in ubuntu..?

---

### Post by lotharmat on 2010-11-04
There is a program called KeePassX - I believe it is in the repositories. Does exactly what you want.

---

### Post by tea for one on 2010-11-04
> **lotharmat said:**
> There is a program called KeePassX - I believe it is in the repositories. Does exactly what you want.

Good morning

I agree, KeepassX is a splendid utility

Kind regards

---

### Post by karthick87 on 2010-11-04
I have used keepassx,it stores username and password in a db file..But what i need is i want to hide all my username and password in Jpeg..Is it possible..?

---

### Post by MartyBuntu on 2010-11-04
> **getyourkarthick said:**
> I have used keepassx,it stores username and password in a db file..But what i need is i want to hide all my username and password in Jpeg..Is it possible..?

Pull up the text file and take a screenshot? Is that what you mean?

---

### Post by Blutkoete on 2010-11-04
No, I think he or she wants to encrypt the password data into a JPG file (e.g. by adding 0 or 1 to each color value) so that there is another security-by-obscurity layer as the person who wants to get his passwords has to know which file they are in.

---

### Post by migs73 on 2010-11-04
You could open a text file, put your info in and the save it. Right click on the file and select rename, change the file extension from .odt to .jpg. This won't actually save it as a jpeg but it will appear so to any one looking at your files.
You will need to right click and 'Open with' then 'other applications..' then select Open office Word proecessor. **Make sure the ' Remember this application for all Jpeg files' is not checked otherwise all Jpegs will try to open with OO.**

Then you have a Jpeg that cannot be opened by the usual picture viewers, but that contains your passwords.

After you have selected with OO WP this will be added to the 'Open with' list , so you don't have to select it from the other list again.

---

### Post by mastablasta on 2010-11-04
since file is not a picture if you put it between other pictures one would immediatelly see that one file didn't display the thumbnail and therefore is hiding something. now all you need to do is check what file type it is, change it to that type and access it with master password (if you know it).

---

### Post by Paresh on 2010-11-04
I believe you want to be looking at steganography.

This is the process of hiding sensitive data in an image so that, to a person without a suitable key, it looks just like a normal picture, but if you have the key, you can extract the hidden data.

I've not used it myself, but there is a program in the repo called steghide.  Not sure how secure it is, but read up and see if it suits your requirements.

---

### Post by migs73 on 2010-11-04
> **mastablasta said:**
> since file is not a picture if you put it between other pictures one would immediatelly see that one file didn't display the thumbnail and therefore is hiding something. now all you need to do is check what file type it is, change it to that type and access it with master password (if you know it).

If you right click on the file it states it is a jpeg. :)

[SIZE="4"]But[/SIZE] (that is a big but)  if you use terminal and the 'file' command it does report as being OO text. :(

I suppose it just depends on who you are trying to prevent getting access to your passwords. A Linux conversant person looking to hack your system who has your master password, or a casual user who may otherwise stumble across, an otherwise unprotected file.

---

### Post by karthick87 on 2010-11-04
> **Paresh said:**
> I believe you want to be looking at steganography.

This is the process of hiding sensitive data in an image so that, to a person without a suitable key, it looks just like a normal picture, but if you have the key, you can extract the hidden data.

I've not used it myself, but there is a program in the repo called steghide.  Not sure how secure it is, but read up and see if it suits your requirements.


Yes this what i need..But if there is a GUI for this it will be better...

---

### Post by Paresh on 2010-11-04
quick search found [this link]("http://stegui.sourceforge.net/").  Again it's not something I've used, so I can't tell you much about it.

I can't see it in the repo, so you will have to read that site carefully and install from there.

Feel free to ask for more help if you get stuck.

Hope it works for you.

---

