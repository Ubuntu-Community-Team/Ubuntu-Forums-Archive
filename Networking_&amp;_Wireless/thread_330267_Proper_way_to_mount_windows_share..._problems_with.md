---
title: "Proper way to mount windows share... problems with &quot;connect&quot; and smbmount"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by Underpants on 2007-01-02
Using 6.10 

This is a cross post to a thread I have in the Multimedia department. I don't know if it should be there, or in here. The problem with #1 below seems mmedia related...

I need to mount a windows share to my ubuntu desktop. There are two ways of achieving this. 

1.“places” and then “connect to server”
This works well. I can read and write where I need to, the mount comes back after a reboot. Looks really good. However, I can't stream mp3's from this location. The files must first be moved to the local hard disk for playback. Searching around shows that this is an issue with 6.10

2.Oldschool “smbmount” Here's the command I'm using
```

 sudo mount -t smbfs -o username=aaron,password=foobar //bluebox/bluebox-data /home/aaron/Desktop/bluebox-data

```

The mount works and I can play mp3's and videos directly from this mount, except I don't think that R/W is working properly. All of the folders have the padlock icon on them. Typing 'mount' in the terminal shows that the share is mounted in Read/Write mode

```

//bluebox/bluebox-data on /home/aaron/Desktop/bluebox-data type smbfs (rw)

```

So, what the hell is going on? Number one I can't stream files over the network. Number two won't let me make any changes. WHO DOES NUMBER TWO WORK FOR!? /end joke.

Seriously. 

Thanks!

---

### Post by Underpants on 2007-01-02
OK. The problem with #2 has something to do with not have super user rights on my ubuntu desktop.  If I open &#8220;sudo gedit&#8221; from the terminal and create a text file, I can save it anywhere on my mounted media. 

WTF.

---

### Post by Iowan on 2007-01-03
What does the **smb.config** look like for that share? Sounds like a **write access** issue.
[http://www.ubuntuforums.org/showthread.php?t=305039]("http://www.ubuntuforums.org/showthread.php?t=305039")

---

