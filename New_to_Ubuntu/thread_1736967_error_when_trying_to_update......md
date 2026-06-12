---
title: "error when trying to update....."
date: 2011-04-22
forum: New to Ubuntu
---

### Post by uniqueone-85 on 2011-04-22
i was trying to update and i ran into this error.....

dpkg: parse error, in file '/var/lib/dpkg/available' near line 34104 package 'avahi-daemon':
 `Depends' field, reference to `dbus': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

any on have any idea what this means......any help will be really appreciated.

---

### Post by frup on 2011-04-22
Is that in the terminal from sudo apt-get update or is update manager spitting that out?

---

### Post by uniqueone-85 on 2011-04-22
it does to both update manager and when i try it in terminal

---

### Post by frup on 2011-04-22
This might not help, but try reconfiguring dpkg. Looks like the problem is something to do with dbus. Have you manually installed anything or done anything unusual? 

sudo dpkg-reconfigure -a

---

### Post by uniqueone-85 on 2011-04-22
hmmm not that i can remember i will try to reconfigure tho

---

### Post by uniqueone-85 on 2011-04-22
ok i tried it and got the same message...

dpkg-query: parse error, in file '/var/lib/dpkg/available' near line 34104 package 'avahi-daemon':
 `Depends' field, reference to `dbus': version contains ` '
/usr/sbin/dpkg-reconfigure: acpi-support is not installed

i am wondering if i may have messed something up when i did my last update. I had to us these commands to get ever thing working:

cd /var/lib/dpkg

sudo cp status-old status

---

### Post by frup on 2011-04-22
Well try

cd /var/lib/dpkg

sudo cp available-old available

---

### Post by uniqueone-85 on 2011-04-23
ok now that i did that i have a new problem......it is saying that i have a broken package. which is ubuntu desktop.....

---

### Post by uniqueone-85 on 2011-04-23
never mind jus had to run apt-get install -f command....that did the trick

---

### Post by uniqueone-85 on 2011-04-23
thanks so much for your help....jus one more question when i run 

cd /var/lib/dpkg

sudo cp status-old status

do i also run

sudo cp available-old available

---

### Post by frup on 2011-04-23
All that command is doing is replacing the file with a back up of itself. I'm not sure what caused the error. You will notice in the error though that it mentions the file "available".

---

### Post by uniqueone-85 on 2011-04-23
oh ok....thanks again then!!!:D

---

