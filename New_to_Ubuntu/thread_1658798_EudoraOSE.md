---
title: "EudoraOSE"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by gandalf69 on 2011-01-03
I just downloaded EudoraOSE and used the following to install it:

Linux
-----

1.  After downloading the file, open up a terminal window.

2.  In the terminal window type in the following:

    sudo tar -C /opt -xvf <place where you downloaded the file>

3.  Then create a link for easy execution by typing:

    sudo ln -s /opt/eudora/eudora /usr/local/bin/eudora

4.  After installation is complete, we recommend that you read the
    README.txt file (this file) in /opt/eudora.

5.  You will then be able to run Eudora from any command prompt
    by just typing in "eudora" (no quotes).


It doesn't work. There is nothing eudora in bin/ but there is heaps in opt/
Are the 'incomprehensible' bits OK?
 
This command prompt stuff brings back PITA memories of DOS3. 
I really appreciate the GUI simplicity of Windows 3.1 and File Manager (or better, Xtree):)

---

### Post by coffeecat on 2011-01-03
> **gandalf69 said:**
> It doesn't work. There is nothing eudora in bin/

Then you forgot to do:

> **gandalf69 said:**
>      sudo ln -s /opt/eudora/eudora /usr/local/bin/eudora


Or you made a typo.

> **gandalf69 said:**
>  4.  After installation is complete, we recommend that you read the
    README.txt file (this file) in /opt/eudora.

Did you?

> **gandalf69 said:**
> This command prompt stuff brings back PITA memories of DOS3. 

Then don't use 3rd party apps whose devs can't be bothered to prepare an installer for the most popular Linux distro. Use an email client that is packaged for easy installation in Ubuntu.

---

### Post by gandalf69 on 2011-01-04
> **coffeecat said:**
> Then you forgot to do:

No.

Or you made a typo.

No, but thanks for the clue, I probably screwed up the <PLACE WHERE IT DOWNLOADED TO>

Did you?

Yes, I read it before d/l

Then don't use 3rd party apps whose devs can't be bothered to prepare an installer for the most popular Linux distro. Use an email client that is packaged for easy installation in Ubuntu.

You have a good point. How do you cut and paste the quotes?

---

### Post by coffeecat on 2011-01-04
> **gandalf69 said:**
> You have a good point.

> **gandalf69 said:**
>  How do you cut and paste the quotes?

If you mean to get the above, like this:

[noparse]> **gandalf69 said:**
> You have a good point.

> **gandalf69 said:**
> How do you cut and paste the quotes?[/noparse]

Forum guide to BBCode: :wink:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

