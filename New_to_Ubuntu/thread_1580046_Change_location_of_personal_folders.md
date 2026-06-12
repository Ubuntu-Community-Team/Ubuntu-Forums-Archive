---
title: "Change location of personal folders?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Sandy106 on 2010-09-22
I just installed ubuntu last night, and was wondering if its possible to change the location of the personal folders like music and photos from the default /home/user/pictures to a different location.

Thanks in advance :)

---

### Post by Jesus_Valdez on 2010-09-22
Just point the relevant software to different folders for the media related.

I don't see why that would'nt work. Ubuntu don't work like windows in that regard (the folders being "coded"), there's just normal folders with an icon.

If you are unsure about that then just put a link inside the folders pointing to the real location of the media.

---

### Post by ubudog on 2010-09-22
Yeah, some commands will do it hopefully, it would be best to back your stuff up onto a flash drive before doing these commands.

```
cd ~/
```

```
mkdir ../nameofnewhomedir
```

```
cp -a Pictures * ../nameofnewhomedir
```

That should do it, but remember to BACK STUFF UP before doing it.

Oh, and "nameofnewhomedir" is the name of your new personal folder or "home directory".

Hope that helps, and welcome to Ubuntu!

---

### Post by Sandy106 on 2010-09-22
> **Jesus_Valdez said:**
> Just point the relevant software to different folders for the media related.

I don't see why that would'nt work. Ubuntu don't work like windows in that regard (the folders being "coded"), there's just normal folders with an icon.

If you are unsure about that then just put a link inside the folders pointing to the real location of the media.

The software in question is ubuntu. I want to change my personal folders (places -> home folder) from the default /home/user/music, pictures, etc. Im not sure how to point ubuntu there, I cant find anything in the options menus.

> **ubudog said:**
> Yeah, some commands will do it hopefully, it would be best to back your stuff up onto a flash drive before doing these commands.

```
cd ~/
```

```
mkdir ../nameofnewhomedir
```

```
cp -a Pictures * ../nameofnewhomedir
```

That should do it, but remember to BACK STUFF UP before doing it.

Oh, and "nameofnewhomedir" is the name of your new personal folder or "home directory".

Hope that helps, and welcome to Ubuntu!

I dont know how to use code, is there a way to change it thru an option menu or something?

---

### Post by Jesus_Valdez on 2010-09-22
What I meant was that just point out the specific software (i.e. Rhythmbox) to the folder with your music (i.e. select your windows partition instead of /home/user/music).

Or you can make a link (right click -> make a link) and then moving that link inside the original folder.

---

### Post by Sandy106 on 2010-09-22
Im not talking about specific software, Im talking about the OS itself. I hate having to dig thru 8 folders to get to my music folder. If I click the music shortcut I want it to open the folder with my music in it. If I click the pictures shortcut I want it to open up the folder that has my pictures in it.

---

### Post by Bölvaður on 2010-09-22
> **Sandy106 said:**
> Im not talking about specific software, Im talking about the OS itself. I hate having to dig thru 8 folders to get to my music folder. If I click the music shortcut I want it to open the folder with my music in it. If I click the pictures shortcut I want it to open up the folder that has my pictures in it.

**find your music folder**, right click it and find **"make link"**
then **cut and paste** this **link into your home** folder (/home/you/link) and **rename the default music folder** (/home/you/Music) into something like Music_bckp

Then **rename your link to Music**

---

### Post by Sandy106 on 2010-09-22
I got an error saying slashes not allowed in filenames

---

### Post by Jesus_Valdez on 2010-09-22
Well, then don't use slashes.



When someone says "/home/USER/Music" what means is "The Music folder inside your Personal folder that is, inside the home folder and under the root folder", so is basically like saying "C:\Documents and settings\USER\Music"

---

### Post by Sandy106 on 2010-09-22
so i type it like homeusermusic?

---

### Post by Jesus_Valdez on 2010-09-22
I think I'm not explaining myself too well, Where do you want to type homeusermusic?

Also, check this:

[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html)

Special attention to the "Creating a Symbolic Link to a File or Folder" section.

---

### Post by cariboo on 2010-09-22
When you see USER in capitals, it means your user name eg:

```
/home/Sandy106/music
```

of course use the user name you created on your computer.

You could also use ~/music which is a sort of shorthand for the above line.

BTW there is no code to be entered, it is the same as entering commands in a Windows cmd window.

---

### Post by ubudog on 2010-09-23
You can execute commands in the terminal.

Applications>Accessories>Terminal.

---

