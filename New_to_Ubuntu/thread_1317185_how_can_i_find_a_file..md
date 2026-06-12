---
title: "how can i find a file."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by yaacovk on 2009-11-06
Hello.
Is there any command to find any file in the software.
for example:
how can i find the Add-ons files of the FireFox.

Thanks in advance.

Yaacov.

---

### Post by ajgreeny on 2009-11-06
I'm not quite sure what you mean, but the firefox add-ons are contained in your home in a folder called **/home/username/.mozilla/firefox/#x#x#x#x.default/extensions.**

If the question is more general have a look at ```
man find
```though I admit that I find the command extremely difficult to get my head around, and the man is pretty useless to me.  I hope you understand it better than me.

---

### Post by Buuntu on 2009-11-06
'find' will phisically search for the file you specify and can take a long time, depending on the size of your hdd/directory you are looking in.  The 'locate' command can be much easier to use and faster because it relies on a database.  However, you usually need to run 'sudo updatedb' to update this database to include new files you have recently added or downloaded.

To find out more about each command:
```
man locate
man updatedb
```

If you want to search for installed packages try:
```
sudo dpkg --get-selections 
```
And if you want to filter that for a specific package, you can do:
```
sudo dpkg --get-selections | grep packagename
```

Also, you probably know about it but Synaptic is a great tool to check for installed applications.  It's located in System > Administration > Synaptic Package Manager and can be a nice GUI for managing packages.

Hope this is what you were looking for...

---

