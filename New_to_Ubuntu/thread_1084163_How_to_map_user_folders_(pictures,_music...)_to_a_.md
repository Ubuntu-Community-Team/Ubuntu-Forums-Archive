---
title: "How to map user folders (pictures, music...) to a local HD (NTSC) ?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Flywaver on 2009-03-01
Greetings,
I am wondering if we can map local folders to folders on a NTFS local drive? For example, I want to point my music and pictures folders to the ones on a separate drive from ubuntu! 

Thanks in advance!
Cheers!

---

### Post by Yashiro on 2009-03-01
It is not clear what exactly you are trying to do.

---

### Post by blueridgedog on 2009-03-01
You can do this with links. 

Lets assume your NTFS drive is mounted as /windows and lets assume on that disk are two folders, one called documents that you want in your home directory as "Documents" and one called pictures you want as "Pictures". [COLOR="Red"] Lets also assume you have safely moved the files out of the local (Ubuntu) folders so that the folders you want to alter are empty.
[/COLOR]
```

cd ~
mv ./Documents ./Documents.orig
ln -s /windows/documents ./Documents
mv ./Pictures ./Pictures.orig
ln -s /windows/pictures ./Pictures
```

(/windows/documents and /windows/pictures are just examples)

Basically you first move any documents you may have in the current Ubuntu directories to a safe place, then you will rename those directories, then replace those directories with links tied back to the folders you want on the NTFS drive.

As a rule I setup my systems to share a "documents" drive and when I first install Ubuntu I delete the empty folders in my home directory and replace them with links to the directories on my documents drive.  I do keep the name so Nautilus sees them.

Once you are satisfied that things have worked as expected and that all of your files are accounted for you can delete the "XXXXX.orig" directories.

---

### Post by cecilieaux on 2011-01-15
There's another wrinkle to this.

I have a Windows XP and applications drive (A), an NTFS documents drive (B), and an Ubuntu 10.10 and applications drive (C).

Windows sees one directory in B as "My Documents," with the usual subdirs (I've even renamed the default folders (My Music to MyMusic) for better Linux use.

Ubuntu has its home directory on drive C -- I'm told that using an NTFS folder for that purpose is problematic -- but I have links from that folder to the folders in B: Docutments=MyDocuments; Music=Mymusic, etc.

Here's the problem:

Programs like Rhythmbox, Banshee, etc., end up with two entries per music or video file.

Entry 1: /home/mydocumentsfolder/mymusic/song1.mp3

(mydocumentsfolder is a link in the NTFS directory in which all documents are stored; mymusic is the music folder in the NTFS drive B, where the music is)

Entry 2 is located at /home/music/song1.mp3

(music is a link to the mymusic directory, directly from the regular Ubuntu home directory)

How do I avoid the double scan of what is essentially one and the same file (song1.mp3?

---

### Post by drpjkurian on 2011-01-15
I was searching for this information for a long time. Let me give a try...

---

### Post by drpjkurian on 2011-01-15
I was searching for this information for a long time. Let me give a try...

---

### Post by drpjkurian on 2011-01-15
I was searching for this inf. Let me give a try........

---

### Post by drpjkurian on 2011-01-15
I was searching for this info. Let me give a try........

---

### Post by Boondoklife on 2011-01-15
This may seem a little obvious, but why not make the music and what not folders separate? Instead of having a link for the entire mydocs folder into your home, why not create a link for just the music,docs, etc?

You could also look into mounting with the bind option, this will allow you to mount your folders on top of others and basically overlay your windows data on top. Again with this option I would just mount the needed folders on top of the empty linux folders as I mentioned, instead of just linking the folder into your home folder.

---

### Post by drpjkurian on 2011-01-15
Sorry for the repetition

---

### Post by cecilieaux on 2011-01-15
> **Boondoklife said:**
> This may seem a little obvious, but why not make the music and what not folders separate? Instead of having a link for the entire mydocs folder into your home, why not create a link for just the music,docs, etc?

You could also look into mounting with the bind option, this will allow you to mount your folders on top of others and basically overlay your windows data on top. Again with this option I would just mount the needed folders on top of the empty linux folders as I mentioned, instead of just linking the folder into your home folder.
I may try your first option. It would mean linking every documents subdir, however, which is a pain. Alternatively, I could link just mydocuments and let the subdir do the trick, without linking the subdirs.

As to mounting with the binding option, or hard link, hmm ... sounds like major surgery I may regret.

---

