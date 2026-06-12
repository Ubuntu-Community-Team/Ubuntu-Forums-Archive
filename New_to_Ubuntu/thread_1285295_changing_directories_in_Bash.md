---
title: "changing directories in Bash"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by luckypunq on 2009-10-07
I am pretty new to Linux environments and BASH, but i did think I had the basics like changing, making and moving directories down. However I am trying to install jdownloader and need to use terminal to do this. When i try to use the command

>  cd /home/dominic/Desktop/JDownloader 0.8.9I get the message that no such directory or file exists. I seem to be doing something wrong, but for the life of me I cannot see what that is.

 It appears from experimenting that the desktop directory is the place where the cd fails.

[IMG]http://tinypic.com/r/14y23yu/4[/IMG]

I would appreciate some help please, as i am sure the solution is both obvious and simple.

TY

---

### Post by NoaHall on 2009-10-07
It's because there's a space in the name. It'd be
```
 cd /home/dominic/Desktop/JDownloader\ 0.8.9/ 
```

---

### Post by cariboo on 2009-10-07
You can't change to the directory by typing:

```
cd /home/dominic/Desktop/JDownloader 0.8.9
```

because there is a space in the directory name. you either have to use quotes eg:

```
cd /home/dominic/Desktop/"JDownloader 0.8.9"
```

or a backslash in the space eg:

```
cd /home/dominic/Desktop/JDownloader\0.8.9
```

Or their is a third way eg:

```
cd ~/JDown*
```

The first two methods will work any time, while the third method will only work if you don't have any other directories call JDown.

---

### Post by DaithiF on 2009-10-07
if there are spaces in the directory name, then enclose in " " , ie.
```
cd "/home/dominic/Desktop/JDownloader 0.8.9"
```
also, since the terminal will open with you already located in your home directory, you can probably reduce your typing a little by omitting the /home/dominic/ part.

---

### Post by sisco311 on 2009-10-07
Use tab completion:  If you type part of a file, command, or pathname and then press the [Tab] key, bash will present you with either the remaining portion of the file/path, or a beep (if sound is enabled on your system). If you get a beep, just press [Tab] again to obtain a list of the files/paths that match what has been typed so far.

Or simply type *cd*, type a space and drag the file/folder in the terminal.

---

### Post by luckypunq on 2009-10-07
Thanks for the useful replies, I have now solved the issue. 

Just want to point out to other newbs that autocomplete isn`t switched on by default (at least not on my installation). The link below showed me how to get that going.

[http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

---

### Post by DaithiF on 2009-10-08
> Just want to point out to other newbs that autocomplete isn`t switched on by default (at least not on my installation). The link below showed me how to get that going.
well the tab-completion of file and directory names should be enabled by default, the other types of bash-completion do indeed require the sourcing of the /etc/bash_completion file.

---

