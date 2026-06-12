---
title: "add and remove applications tab not working???"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by narutarded on 2010-04-28
when ever i click on the add and remove tab it says 

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

and nothing comes up...everythings grey. i don't know what to do...any help? i'm screaming right now becuz my systems is all wack and i don't know when i'll be able to install windows 7.  i have linux ubuntu 8.10 right now(it came with my laptop). how can i fix this problem?

---

### Post by marshmallow1304 on 2010-04-28
Open a terminal (Applications->Accessories->Terminal) and run
```
sudo apt-get update
```
You will need to enter your password when prompted.  If there are any errors in /etc/apt/sources.list they will be mentioned in the output.  If there aren't, go ahead and run
```
sudo apt-get install -f
```

---

### Post by narutarded on 2010-04-28
when i type in  
"sudo apt-get update"
the out put is:
E: Type 'ndeb' is not known on line 44 in source list /etc/apt/sources.list

same thing when i type in
"sudo apt-get install -f"
the out put is:
E: Type 'ndeb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.

any the add an remove app still doesn't work. :/

---

### Post by warfacegod on 2010-04-28
> Please check for broken packages with synaptic...

This is a key phrase. (But may not be the only one.)

Go to: System> Admin.> Synaptic Package Manager> click Edit menu (top left)> select Fix Broken Packages.

---

### Post by ajgreeny on 2010-04-28
Try ```
gksudo gedit /etc/apt/sources.list
```in terminal.  That file will open up in your text editor and you can then go to line 44 and edit out the word "ndeb", which appears to have crept in somehow, and replace it with just "deb", ie just delete the "n".

Also bear in mind that 8.10 is bout to loose any further support, so an upgrade or new install would be better.  Let's get 8.10 running properly first, then think about where to go from here.

---

### Post by narutarded on 2010-04-29
hey thanks [ajgreeny]("http://ubuntuforums.org/member.php?u=27747")

i ended up deleting all my Ns in every "ndeb" and it's working now. i'm so happy! thank you soooo much! :D

---

