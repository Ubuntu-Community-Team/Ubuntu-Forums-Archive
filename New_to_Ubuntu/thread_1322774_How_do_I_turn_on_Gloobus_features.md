---
title: "How do I turn on Gloobus features?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by the8thstar on 2009-11-11
Hello,

I installed Gloobus (a preview manager like in OSX), but I can't get the full thing to work in Nautilus. If I select a file and press space, I do get a preview (see screenshot), but there's no way to get a preview of all the files in the folder (the coverflow effect).

Anyone knows how to fix this?

Here is the output from the command line:

> the8thstar@the8thstar-laptop:~$ gloobus-preview
Getting file from clipboard
Filename: 
ClipBoard: /home/the8thstar/Downloads/Monaco.ttf
LOADING PLUGINS:
	 /usr/lib/gloobus/audio.so
	 /usr/lib/gloobus/comic.so
	 /usr/lib/gloobus/folder.so
	 /usr/lib/gloobus/icns.so
	 /usr/lib/gloobus/openoffice.so
	 /usr/lib/gloobus/pdf.so
	 /usr/lib/gloobus/pixbuf.so
	 /usr/lib/gloobus/text.so
	 /usr/lib/gloobus/ttf.so
	 /usr/lib/gloobus/video.so
CONTENT FOLDER: /home/the8thstar/Downloads

(gloobus-preview:8438): GLib-GIO-CRITICAL **: g_file_info_get_attribute_string: assertion `G_IS_FILE_INFO (info)' failed
Segmentation fault

---

### Post by s1.ranjan on 2009-11-18
I am too having the same issue#-o, i.e., coveflow effect is not working and i think this can be solved by Gloobus on fire  where as if you want to move between different file in Gloobus it can be achived by using left and right arrow keys ;) and you can get more information from [gloobus]("http://gloobus.wordpress.com/") ](*,)

---

### Post by kimda on 2009-11-19
Here are instructions how you can install it for Ubuntu 9.04 and 9.10. 

[http://gloobus.net/download/](http://gloobus.net/download/)

---

