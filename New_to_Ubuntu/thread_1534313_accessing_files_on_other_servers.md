---
title: "accessing files on other servers"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by etosch on 2010-07-19
Hello, Ubuntu community. This is my first post.

I recently switched over to Ubuntu from XP and have been using my personal laptop at work. I'm doing some coding in Python that involves reading files from a shared space on a Netapp server. How do I reference said server? I'm basically looking to translate \\server\shared_folders\my_shared_folder\my_file.txt into something appropriate for the python os module.

If there's another thread where this is already answered, I apologize for the redundancy; I didn't have any luck searching for an answer to this one.

Thanks!

---

### Post by cariboo on 2010-07-19
Depending on how netapp shares files, you should be able to access your files by going to Places->Network, and entering the path to your files.

---

### Post by Linux000 on 2010-07-19
Do you need to get to the files on your computer, or are you trying to get the program to access the files?

---

### Post by etosch on 2010-07-19
@cariboo907 I know the path already - I just know it using Windows path constructions. The issue is getting the equivalent path in a form that my Ubuntu file system understands and can be parsed by the os Python module. So, going through the GUI won't cut it. 

@Linux000 I need my Python program to access the files. I just need to know how to reference it from my program. So as I said, something that is like a translation of \\servername\shared_folder\sub_folder\myFile is what I'm looking for.

Thanks for the replies!

---

### Post by Linux000 on 2010-07-19
You could have the system mount the volume so it appears as a local file(even though it is in the server) and then open it in python.

---

### Post by Morbius1 on 2010-07-19
> I'm doing some coding in Python that involves reading files from a  shared space on a Netapp server. How do I reference said server? I'm  basically looking to translate  \\server\shared_folders\my_shared_folder\my_file.t  xt into something  appropriate for the python os module.I may be reading far more into that sentence than you intended but it appears as though you already have it mounted. Did you go to Network and access the server to see if you can find the "my_file.txt" file?

If so then your remote share is already mounted at this location:
```
/home/your_user_name/.gvfs
```And the full path to the file itself would be:
```
/home/your_user_name/.gvfs/"shared_folders on server"/my_file.txt
```Go into Nautilus and go to your .gvfs folder and find the txt file and you'll understand the path more clearly.

---

