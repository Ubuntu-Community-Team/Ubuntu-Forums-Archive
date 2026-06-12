---
title: "Webcam and FTP program that archives multiple images?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Razmear on 2009-05-21
I've installed about a half dozen packages with no joy. 
Here is all I'm trying to do, I have a working webcam and I want to capture an image every 30 seconds and upload that image to my webhost with a unique filename for each picture. 
The filename can increment up, use date/time info, or any other method. The most recent file does not have to have any special name or other considerations (as is done in some webcam software). 
webcamd would be perfect if it would archive more than the latest image. I tried hacking the perl script to $date.$time.webcam.jpg but no joy there either, and I'm no perl guru (or even a novice) so not much hope there. 

The reason for this request is a neighbor ran off someone trying to climb into my living room window about a week ago, so I want a lightweight app running that captures a pic every 30 seconds (not motion, just a pic every 30 seconds) then punts those pics to my webserver so if I come home and find my house ransacked I can ftp to the latest pics and see who did it. I can manually delete the pics in the event my web host starts to fill up, and I'd prefer to save all images, not just the last 100 or 1000 or so. 

Thanks for any pointers you can offer,
eb

---

