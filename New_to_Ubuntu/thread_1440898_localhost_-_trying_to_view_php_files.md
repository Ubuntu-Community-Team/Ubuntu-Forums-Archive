---
title: "localhost - trying to view php files"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by issachan on 2010-03-28
Hi all,

I installed apache2 with php on my computer and I know it's working, I've restarted it, and it's happily displaying files in the www folder. However, for organization purposes I'm trying to organize my files into folders and preview them before I upload them to my web host. I can view it only if it's directly in the www folder but it refuses to display it in any child folders.

Help! What am I doing wrong? :-|

---

### Post by Paqman on 2010-03-28
How are you trying to view them? Have you checked permissions on the folders and files?

---

### Post by s_ø on 2010-03-28
Is the subfolders inside the www directory?
What do you mean by "refuse to display"?
In firefox? Does it give you an error of some sort or just a blank page?

---

### Post by issachan on 2010-03-28
The files are located in a folder I named DFMC and I put it in the www folder. When I try to open them it keeps popping up a window asking me to save it or open it with one of my php file editors. 

I have checked the permissions and I had set them to be under my user account but accessible by all others. I also tried checking and unchecking the option to "Allow executing file as program" but it had no effect.

Any ideas? 

Thanks for your help :D

---

### Post by s_ø on 2010-03-28
If you open the php files directly, apache wont parse it.
You need to open them in your browser via localhost.
[http://localhost/]("http://localhost")
[http://localhost/DFMC](http://localhost/DFMC)

---

### Post by Paqman on 2010-03-28
> **issachan said:**
> When I try to open them it keeps popping up a window asking me to save it or open it with one of my php file editors. 


Are you trying to edit the actual PHP file, or do you want to see the HTML that a visitor would see? If it's the latter then as s_ø said, you need to run it through Apache and view it in your browser.

---

### Post by issachan on 2010-03-28
Yay! It's working! Thanks everybody! :D

---

### Post by s_ø on 2010-03-28
You are welcome. Please mark thread as solved.

---

