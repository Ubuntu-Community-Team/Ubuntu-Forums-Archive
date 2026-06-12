---
title: "How Do I Remove Me as User??"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by padrejeff on 2008-12-13
Crazy Title, I know. 

However, I am selling my IBM laptop with dual boot Win XP Pro and Ubuntu installed.

I would like to remove me and the my login prompts for user and password and let the new owner set up his/her own.

I'm relatively new to linux (have it installed on my new laptop though) so not sure how to do this. I want to give them a usable OS, but don't want them to have to type in my user name and password to boot fully.

Thanks,

Jeff

---

### Post by cmay on 2008-12-13
you can change your name and password to something else. when install ubuntu for others i do this with a standard username and passwd i can always rmeber and leave a txt file on the desktop with the instructions on how to change it. it is in user and groups you do that. 
hope it helps.

---

### Post by Bonger1901 on 2008-12-13
I recommend formatting your drive and re-install the operating system. The buyer will most-likely just want Windows on it anyway?

---

### Post by agathian on 2008-12-13
I think you should be able to login as root and remove/modify other user accounts..

Typically root login is not allowed via gui. you could get to command line login by pressing ctrl-Alt-F1[F2,F3,etc].

But if you are not comfortable with command line, then you could enable gui login for root by

System->Administration->Login Window->Security

and select "System Administrator Login". 

i think, you should be able to logout and login back as user.

[ I am assuming you have root password set already.., if not type "sudo password" and set it up "

Hope this helps..

---

