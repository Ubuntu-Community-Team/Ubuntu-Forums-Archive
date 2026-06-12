---
title: "Apache Case-insensitive"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by PJOS13 on 2011-01-10
Hi, recently I've been migrating my development environment to ubuntu (desktop edition, because this is not a server, is just my computer) and I've been having some problems with apache case-sensitive (I'm an absolute beginner with it).

I want to make apache case-insensitive, but I didn't find a complete and easy to follow solution online more than doing this:

[LIST=1]
[*]From the command line, type sudo su to get root privileges.
[*]nano /etc/apache2/mods-available/speling.conf
[*]Type CheckSpelling on and hit ctrl-x, y to exit and save the file.
[*]type a2enmod and then speling and hit enter.
[*]type /etc/init.d/apache2 reload to reload apache.
[*]Mistype a url to test it.
[/LIST]

I found that here: [http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/](http://keystoneit.wordpress.com/2007/02/19/making-apache-case-insensitive/)

It worked for some things but I'm still having a lot of problems with capitalization. Any suggestions? :confused:

Please, help me! I don't wanna go back to windows an ISS. And fixing my file name by hand won't be a solution it will take to long. :(

BTW I'm using ubuntu 10.10 desktop edition 32-bits, and I've not moved any apache configuration more than that described above.

---

### Post by PJOS13 on 2011-01-10
at least someone knows how to configure the rewrite module?:confused:

Helps please!! :(

---

### Post by bodhi.zazen on 2011-01-10
I am not sure how to configure Apache to do this, but there are a number of scripts to write your files all lower case (google search and you will find them).

Work of a copy of your files ;)

I would think mod-rewrite would be impractical, it would take as much time to write the rules as it would to manually rename the files.

---

### Post by PJOS13 on 2011-01-10
Well, my problem is not simply the files names, I can lower case them all, but I will also need to fix the folders names and the files themselves.

Suppose I have a HTML file pointing to a CSS style-sheet located in "var/www/TESTS/Style.css" and that the path I used to point at it in the HTML file was "VAR/test/style.CSS".

Thats my problem, so I have to fix more than one thing and I hadn't found a script capable of doing this.

Thank you for your answer anyway :D I really appreciate your help.

---

### Post by bodhi.zazen on 2011-01-11
> **PJOS13 said:**
> Well, my problem is not simply the files names, I can lower case them all, but I will also need to fix the folders names and the files themselves.

Suppose I have a HTML file pointing to a CSS style-sheet located in "var/www/TESTS/Style.css" and that the path I used to point at it in the HTML file was "VAR/test/style.CSS".

Thats my problem, so I have to fix more than one thing and I hadn't found a script capable of doing this.

Thank you for your answer anyway :D I really appreciate your help.

Well, there is always a chance you may need a major re-write to your web pages. This should not be *too* bad. From your post it sounds as if you have the basic setup done "right" with separate style sheets.

Take a look at sed, you can automate or script much of the update.

Again, be sure to work on a copy.

```
sed -i -e 's_var/www/TESTS/Style.css_var/www/tests/style.css_g' file.html
```

sed can also change upper to lower case as can tr (google search and you will find several examples and several scripts you can likely either use directly of modify).

See man tr and look at sed

---

### Post by PJOS13 on 2011-01-11
Thank you for your help, I'll try it and post here if it works.

---

### Post by bodhi.zazen on 2011-01-11
> **PJOS13 said:**
> Thank you for your help, I'll try it and post here if it works.

If you have problems , just ask. People here can probably help with the scripting, but we need details, what needs to change and what do the directories and files look like ?

---

### Post by PJOS13 on 2011-01-12
I used the CheckCaseOnly directive in apache and almost everything worked well, now I can correct the remaining problems by hand.

Thank you for your help. Anyway I'll search the script 'cause I think is better to have a standard, If I got a question I'll post a reply.

---

### Post by PJOS13 on 2011-01-12
Sorry I posted twice, my internet connection failed in the moment I pressed the post button.

---

### Post by bodhi.zazen on 2011-01-12
Sounds as if you are up and running. +1 on converting your files as time allows =)

---

### Post by PJOS13 on 2011-01-12
By the way, I have another question about where to find and how to configure an Informix connector for Ubuntu, but I don't know where to ask. 

With the Apache question the only place I found an answer was the 'absolute beginner talk' I didn't get luck in the other forums.

So where should I ask that?

---

### Post by bodhi.zazen on 2011-01-12
I have no idea what an Informix connector is, lol

Google ?

If it is a windows or proprietary application you may want to find an opensource alternate ?

---

### Post by PJOS13 on 2011-01-12
Don't worry, I was just asking which was the best board to ask a question like that :wink:. That connector is the last thing I need to change all my infrastructure to Ubuntu.

---

