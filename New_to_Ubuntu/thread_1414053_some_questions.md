---
title: "some questions"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by en_mohamed on 2010-02-23
hello dears
i have 5 ques:
1-i want to know where the installed programs put like mplayer,vlc as in windows there are in program files
2- i want to change the name of my partitions ,when i try to change them the message is shown(Sorry, could not rename "60 GB Hard Disk: DISK1_VOL2" to "hnn": Operation not supported by backend).
3-some sound files when i played them in movi player the file name is shown with  strange shape like this(~@#$%#)
4-every once i logg in my system and try to open partitions it needs to authorize and write the pass word &#1548; i want to cancel this authorization
5- the button which control in (upper case &lower case is left control button)i want to change 
it to be capsloock, how?
sorry about the long ques.

---

### Post by nothingspecial on 2010-02-23
1 - Usually /usr/bin or /bin, sometimes /usr/sbin /sbin

2 -```
sudo apt-get gparted
``` open it up type your password and change the names. You have to unmount any partition you want to relable first. 

3 - Are these normal file name? What are they supposed to be?

4 - Change the ownership of the partitions to your user. Find the full path to each partition in your file browser. It should be something like /media/disk. Then ```
sudo chown -R username:username /media/disk
```. Change both usernames to your real username and the path to the actual path.

5 - Sorry, don`t know

---

### Post by en_mohamed on 2010-02-23
> **nothingspecial said:**
> 1 - Usually /usr/bin or /bin, sometimes /usr/sbin /sbin

2 -```
sudo apt-get gparted
``` open it up type your password and change the names. You have to unmount any partition you want to relable first. 

3 - Are these normal file name? What are they supposed to be?

4 - Change the ownership of the partitions to your user. Find the full path to each partition in your file browser. It should be something like /media/disk. Then ```
sudo chown -R username:username /media/disk
```. Change both usernames to your real username and the path to the actual path.

5 - Sorry, don`t know
thank you very much mr nothingspecial:P

---

### Post by en_mohamed on 2010-02-23
4 - Change the ownership of the partitions to your user. Find the full path to each partition in your file browser. It should be something like /media/disk. Then ```
sudo chown -R username:username /media/disk
```. Change both usernames to your real username and the path to the actual path.


sorry i did not understand this thing ,i hope you understand me this line in terminal

---

### Post by en_mohamed on 2010-02-23
hello dears 
again i want from us to reply about the last three question

---

### Post by nothingspecial on 2010-02-23
When you have mounted your partitions they will exist somewhere within the file system. Usually in /media.

You want to change the ownership of those drives to you. The command to do this is chown ([COLOR="Red"]ch[/COLOR]ange [COLOR="Red"]own[/COLOR]er)

As you don`t own them you have to do this as root - sudo

-R means to change every folder and file contained within the folder you are changing ownership of 

username:username makes the folder owned by the specified user:group (yes you have a group too)

You need to find out where your partitions are mounted. If you have already renamed them then they should be at /media/whatever_you_called_them.

Assuming your username is mohamed, the command in a terminal would be

```
sudo chown -R mohamed:mohamed /media/new_name_of_partition
```

I hope this explains it more clearly although I can understand if this has made it worse.

---

