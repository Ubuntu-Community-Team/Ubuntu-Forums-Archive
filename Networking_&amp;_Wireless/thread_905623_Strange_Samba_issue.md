---
title: "Strange Samba issue"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Carl H on 2008-08-30
I have a something peculiar going on with a Samba share that I've just set up. My photo collection is on my Xubuntu box, and I've set it up to share it so that my wife can view it on her XP box. 

It all seems to work fine, except some of the pictures just produce a "Can't be displayed" type of error on the XP machine - even though they look fine on my Xubuntu box. A lot of the pictures were taken with the same camera, so I don't think dodgy jpg files are the cause. 

Could it be something like permissions or maximum file size? 

Or any other suggestions?

---

### Post by bab1 on 2008-08-30
How many users have access to the "share"?   Just a guess here, but I would see what the file permissions and ownerships are.  Post the results of the directory where the pictures are located. You can use; ```
ls -l
``` from the terminal.

Also post the spec's from the smb.conf on the "share" in question.

---

### Post by Carl H on 2008-08-31
ls -l
```
drwxr-xr-x  9 carl carl   4096 2008-08-30 16:42 2002
drwxr-xr-x 21 carl carl   4096 2008-08-30 16:42 2003
drwxr-xr-x 13 carl carl   4096 2008-08-30 16:42 2004
drwxr-xr-x 10 carl carl   4096 2008-08-30 16:42 2005
drwxr-xr-x  2 carl carl   4096 2008-08-12 11:15 BBQ  27th July 2008
drwxr-xr-x  2 carl carl   4096 2008-02-15 22:07 Blackpool, 13th Feb 2008
drwxr-xr-x  2 carl carl   4096 2008-01-10 19:05 Calf Hey, 6th Jan 2008
drwxr-xr-x  3 carl carl   4096 2007-09-30 11:04 camera_dump
drwxr-xr-x  2 carl carl   4096 2008-03-17 20:29 Debbie & Nobby's wedding, 8th March 2008
drwxr-xr-x  2 carl carl   4096 2008-01-11 13:01 December 2007
drwxr-xr-x  2 carl carl   4096 2008-05-06 08:32 Doctors & Nurses Do, Sunday 4th May 2008
drwxr-xr-x  2 carl carl   4096 2006-11-09 13:47 ellie_christening
drwxr-xr-x  2 carl carl   4096 2008-04-24 21:09 Fuerteventura, March 2008
drwx------  2 carl carl  20480 2007-05-08 18:42 Norway 2006
drwxrwxrwx 20 carl carl   4096 2007-02-12 17:58 Scott
drwxr-xr-x  2 carl carl   4096 2008-03-17 20:28 Scott in bed, 27th Feb 2008
drwxr-xr-x  2 carl carl   4096 2008-02-02 13:50 Scott in the snow, 2nd Feb  2008
drwxr-xr-x  2 carl carl   4096 2008-03-17 20:29 Scott & Samuel eating and drinking, 9th March 2008
drwxr-xr-x  2 carl carl   4096 2008-02-22 17:04 Scott's Big Bed, 21st Feb 2008
drwxr-xr-x  2 carl carl   4096 2008-02-10 19:47 Scott's birthday
drwxr-xr-x 47 carl carl   4096 2008-08-30 16:41 Scott - the early years
drwxr-xr-x  2 carl carl   4096 2008-02-15 22:07 Southport, 11th Feb 2008
drwxr-xr-x  2 carl carl   4096 2007-10-30 19:20 Tenerife 2007
drwxrwxrwx  2 carl carl   4096 2006-06-02 13:41 Tracey
```

smb.conf section:
```
[Photos]
path = /home/carl/Photos
available = yes
browsable = yes
public = yes
writable = no
```

---

### Post by bab1 on 2008-08-31
Are you the only user?

As an example this:> drwx------  2 carl carl  20480 2007-05-08 18:42 Norway 2006 is very different that this:> drwxrwxrwx 20 carl carl   4096 2007-02-12 17:58 Scott

Using a lot of subdirectories means you have to be very consistent with your permissions from the beginning.

Let's do  a simple test.  From the Xubuntu box make a directory (folder) in this share. We can call it **[COLOR="Blue"]test[/COLOR]**.  Make sure that you can create, view and delete files in that folder.  If you are the only user on the system then the default permissions should be fine.  Now copy some of the pictures [COLOR="Red"]you can NOT open[/COLOR] into the **[COLOR="Blue"]test[/COLOR]** folder.

Now see if you can vies the pictures from XP.

Let me know the results.  What we are trying to determine is where the permissions are restricting the user from accessing the file.

---

### Post by Carl H on 2008-09-18
My apologies, I thought I had already replied to this. 

I was confusing the Samba "Read Only" permission with the file permissions on the disk. I quick chmod on the top directory, and all the files are now available for viewing on the Windows PC. 

Thanks for the tip, and my apologies again for not replying before now.

---

