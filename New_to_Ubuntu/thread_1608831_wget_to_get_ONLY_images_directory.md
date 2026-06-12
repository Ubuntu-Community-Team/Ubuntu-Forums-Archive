---
title: "wget to get ONLY images directory"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by smoh on 2010-10-29
Hey All,

I'm an absolute ubuntu and linux noob all together.  I just discovered the wget function which works perfectly for what I need to do.  I'm trying to download my /images directory.  I've tried to do wget -m mydomain.com/images but it ends up downloading everything from my domain which is not what I want at all. 

If anyone can help with a wget function JUST to get all of the files from my /images directory, that would be great! I'm using ubuntu server version right now and have successfully set up dedicated server there.

---

### Post by gmargo on 2010-10-29
Try adding the **--no-parent** option.

---

### Post by smoh on 2010-10-29
Hi,

I tried wget -np mydomain.com/images and it saves a file but doesn't actually get the rest of the images directory that I want. 

It saves a file as images with no specific file type. Here's what terminal spits out to me...


...........
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.mydomain.com/images/](http://www.mydomain.com/images/) [following]
--2010-10-29 22:03:23--  [http://www.mydomain.com/images/](http://www.mydomain.com/images/)
Connecting to [www.mydomain.com|ipaddress|:80](www.mydomain.com|ipaddress|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `images'


Any ideas on how I can get this?  What about the child folders as well? For example mydomain.com/images/folder1/subfolder1

---

### Post by smoh on 2010-10-29
Quick update...

Adding the slash at the end of /images/ gives me an html file with the file names, but not the actual images itself.  Any ideas on how I can download the entire directory?

---

### Post by gmargo on 2010-10-30
Why did you remove the **--mirror** (-m) option?

---

### Post by joshruehlig on 2010-10-30
/images/*.jpg /images/*.png (ect)
This will grab all jpg's and png's in you image directory

---

### Post by smoh on 2010-11-01
> **joshruehlig said:**
> /images/*.jpg /images/*.png (ect)
This will grab all jpg's and png's in you image directory

Thanks for your help ladies and gents.  It still isn't working now. I'm getting a 404 Not Found error when I try to do something like wget -np [http://www.mydomain.com/images/*.jpg](http://www.mydomain.com/images/*.jpg) 



wget -m [http://www.mydomain.com/images/*.jpg](http://www.mydomain.com/images/*.jpg) 

Gives the same error as well. Any reason why this would be happening? This is so frustrating :(

---

### Post by smoh on 2010-11-01
Just figured it out.  It was a combination of what everyone said..

For anyone looking...

wget -m -np yourdomain.com/images/

---

