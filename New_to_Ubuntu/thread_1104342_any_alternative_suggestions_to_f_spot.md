---
title: "any alternative suggestions to f spot?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by nickstephens on 2009-03-23
hi, 

I am trying to retrive the avi files from my digital camera. I have a gutsy machine that provides links to the place where my photos and videos are stored on the camera. In addition gthumb works. 

Then I have a hardy machine with this bloody f-spot which can not download avi files. You can see the usb mount and f spot (which irritates the hell out of me by seperating everything in terms of dates but thats another rant) convieniently appears to windowsify a process that was working perfectly well before! Anyway, I have been trawlling the forums and I can't find a decent way to extract my avi files (addtionally annoying as gthumb no longer appears to work) or find the mounted files. I don't really understand why I can't find the mounted camera drive or create an adequate mount if the camera is listed. 

Any suggestions as it is bugging the s*** out of me to borrow my girlfriends windows machine to download the avi files!

---

### Post by ugm6hr on 2009-03-23
Plug the camera in (presumably USB), and then try and find it in:
```
sudo fdisk -l
```

It should be there if it worked with Gutsy.

You can try and find its mount point in:
```
df -h
```

---

### Post by nickstephens on 2009-03-24
In response to earlier comment. I uninstalled f-spot and have gthumb back and working. The digital camera will not autodetect anymore now there is a missing link, although there is the message asking if I want to import my photos. Gthumb also protests about not being able to find certain locations but these are ignorable error messages.

I can however download my avi files so I am happy and I will try and sort out auto-detect issue when I have 5 mins. I wonder if f-spot really should have been shipped as standard though! I know it is a package that is supposed to make things easier but it's windows-like qualities make it a pain to get around.

---

### Post by tekkieguy on 2009-03-24
Google's Picasa Program in now avalible for Linux, instaed of just runniong it through Wine. It works really good i think and it imports my photos great

---

