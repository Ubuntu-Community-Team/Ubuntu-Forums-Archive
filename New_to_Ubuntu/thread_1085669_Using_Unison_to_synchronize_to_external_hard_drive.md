---
title: "Using Unison to synchronize to external hard drive (NTFS)"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2009-03-03
I wanted to start backing up my laptop and got an external hard drive. Upon doing some searching Unison seemed like the best choice since it just synchronizes the updated files. However every time I create a new file Unison has an issue moving it over to the hard drive.

My issue is very similar to the one jlacroix had in this thread 
[http://ubuntuforums.org/showthread.php?t=929180&highlight=unison+backup+hard+drive+ntfs]("http://ubuntuforums.org/showthread.php?t=929180&highlight=unison+backup+hard+drive+ntfs")

I am running Intrepid Ibex on a Lenovo 3000 v100. The external hard drive is a 1TG Seagate freeagent formatted to NTFS

Thanks in advanced

---

### Post by Kellemora on 2009-03-03
Hi Tad

I couldn't get Unison to do what I wanted it to either.

Have you tried GRsync, it's graphical and seems to work quite well.

I had some issues with it also at first, but most of those were that I had not set up the correct permissions for the drive needing to be written to.

Also, as far as syncing files, we hit the same problems I had way back on day one when I first started using Linux appear again.  And that is you cannot PUT anything anywhere, but you can FETCH everything.

If you have more than one computer and you need the data from computer A stored on computer B, use computer B to fetch the data from computer A's shared folders.

Or simply said, I have a data file server, and every time I think a file is saved to it, it's not there, with no warnings either.
So I've made it standard practice around here, re instituted an early law I had initiated in this place.  Save your NEW files to the shared desktop folder and let the File Server fetch them from your machine for storage.

By doing it this way, we do not lose files we thought were saved, but weren't.  Neither Gimp nor Open Office will SAVE a file to the file server, but makes you THINK it did.  Then when you go to fetch it, it's not there.  Until Cron runs Rsync and pulls all the new files from the various computers.  Once they are in the File Server, then anyone can access and edit them and they save back to the File Server as expected.

I have signs all over the office here, PUT don't work but Fetch DO!

TTUL
Gary

---

### Post by TadeoDiaz on 2009-03-03
Thanks for your response Gary, I will definitely check out GRsync and see if that is easier to set up than Unison. I am currently running two computers: My laptop which is strictly for school work and my tower which holds all of my music, photos, and archives the school files. In the past I had been transferring all the school files at the end of the semester but since my computer is getting older I started getting paranoid that I would lose everything if my hard drive died.

Ill let you know how GRsync works.

Tadeo

---

