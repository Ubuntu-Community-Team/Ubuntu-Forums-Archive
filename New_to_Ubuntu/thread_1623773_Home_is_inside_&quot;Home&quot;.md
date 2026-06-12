---
title: "Home is inside &quot;Home&quot;"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by daethyme on 2010-11-17
When I boot up in 10.10 I get the no home file and no ICEauthority note. I boot up ok when I close the note but when I go to Places-Home my audacious music player loads and starts playing music.
I went into "computer" and file system, opened my Home folder and my Home folder, named daethyme is inside it. So, to be clear, my home folder is inside my "Home" folder and I can't move it into my file system because "you do not have permission to do this".
I've spent hours looking at posts but nothing speaks to this that I can see. 
There must be a way to reconfig. this and I'm sure someone out there knows this, so thank you in advance.
I have an external HD of 500 GB that I've disconnected thinking it was the problem. It's not. I just upgraded from a fresh install and am still getting everything "in place". Directions should be step by step and clear. I'm fairly new at this.
peas n' bugs :(
daethyme

The File association thing worked. Thank you.:)

---

### Post by Verbeck on 2010-11-17
> **daethyme said:**
>  when I go to Places-Home my audacious music player loads and starts playing music.

sounds like a problem with file associations..
on your desktop, create a new folder(if you dont have one) and right click it and select 'open with other application'. from the list choose 'file browser' and make sure the 'remember this application' is checked
> **daethyme said:**
> 
I went into "computer" and file system, opened my Home folder and my Home folder, named daethyme is inside it. So, to be clear, my home folder is inside my "Home" folder and I can't move it into my file system because "you do not have permission to do this".

/home contains all the users home folders. it itself is not the user's home directory

the home folder for user X would be /home/X
for user Y, it would be /home/Y

hope this helps

---

### Post by wiznillyp on 2010-11-17
Have you tried booting to a command line and moving the Home folder to the proper location?

---

### Post by daethyme on 2010-11-17
> **Verbeck said:**
> sounds like a problem with file associations..
on your desktop, create a new folder(if you dont have one) and right click it and select 'open with other application'. from the list choose 'file browser' and make sure the 'remember this application' is checked


/home contains all the users home folders. it itself is not the user's home directory

the home folder for user X would be /home/X
for user Y, it would be /home/Y

hope this helps

Thank you. That worked it out. I thought I remembered under 10.4 that my Home opened as my /home/y and was listed as that in my tree. Maybe not. Anyway, this worked for association and stopped the music. Regards. daethyme

---

