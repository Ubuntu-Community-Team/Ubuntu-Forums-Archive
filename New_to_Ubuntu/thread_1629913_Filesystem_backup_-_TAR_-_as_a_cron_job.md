---
title: "Filesystem backup - TAR - as a cron job"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-24
It's easy enough to start a tar backup from the command line because you can actually navigate to the root directory.

But as a Cron Job, how do you specify that the TAR command should be on the entire filesystem ?

Would you add a slash like this......?

sudo tar cPzf tarfile.tar **[SIZE="6"][COLOR="Red"]/[/COLOR][/SIZE]** --exclude=/blah blah blah


or....

do you use a input to command directive such as 

cd /

---

### Post by mistypotato on 2010-11-24
-C, --directory DIR

[COLOR="Gray"][SIZE="1"]Source: [http://linux.about.com/od/commands/l/blcmdl1_tar.htm]("http://linux.about.com/od/commands/l/blcmdl1_tar.htm")[/SIZE][/COLOR]

    change to directory DIR
so an example.....

sudo tar cvPf /filesystem.tar -C /  --exclude=/blah blah blah

or

if you take the syntax somewhat literally....

sudo tar cvPf filesystem.tar -C, --/ DIR? --exclude=/blah blah blah


Now here's an example where the "-C" was not used at all......

tar -pczf mywebsites.tar.gz /var/www/ --exclude "/var/www/mydomain/images/" --exclude "/var/www/otherdomain/pictures" 

[COLOR="Gray"][SIZE="1"]Source: [http://www.wallpaperama.com/forums/how-to-exclude-a-directory-in-a-tar-linux-command-t6486.html]("http://www.wallpaperama.com/forums/how-to-exclude-a-directory-in-a-tar-linux-command-t6486.html")[/SIZE][/COLOR]

Head spinning yet  :P
kinda confusing isn't it ?


Googling is great, but you often have to do a LOT of research and interpolation to get your answer.
My vote is that if an example is provided, a thorough explanation of each part (even those assumed to be understood) should accompany it.  

After diligent research, I still don't know (from Googling and reading) what to do....SO...I will solve this via experimentation.
 ):P[SIZE="1"][/SIZE]

---

### Post by mistypotato on 2010-12-04
I just used a slash

---

