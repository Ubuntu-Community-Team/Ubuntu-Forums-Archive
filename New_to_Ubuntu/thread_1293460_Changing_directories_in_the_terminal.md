---
title: "Changing directories in the terminal"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by triggerchar on 2009-10-17
Hi please please please help  
 

 I am newbie and would be very grateful for any kind of help.
 I cant see any folders below my home folder for example
 

 trigger@trigger-laptop:~$ cd /home/trigger/desktop 
 bash: cd: /home/trigger/desktop: No such file or directory 
 trigger@trigger-laptop:~$  
 

 but I can see all the folders using ls command  
 

 trigger@trigger-laptop:~$ cd /home/trigger 
 trigger@trigger-laptop:~$ ls 
 Desktop            sdc10043.jpg  sdc10096.jpg  sdc10124.jpg  sdc10159.jpg 
 Documents          sdc10045.jpg  sdc10097.jpg  sdc10125.jpg  sdc10160.jpg 
 examples.desktop   sdc10051.jpg  sdc10098.jpg  sdc10126.jpg  sdc10161.avi 
 libflashplayer.so  sdc10053.jpg  sdc10099.jpg  sdc10127.jpg  sdc10162.jpg 
 Music              sdc10057.jpg  sdc10100.jpg  sdc10128.jpg  sdc10163.jpg 
 Photos             sdc10059.jpg  sdc10101.jpg  sdc10129.jpg  sdc10164.jpg 
 Pictures           sdc10061.jpg  sdc10102.jpg  sdc10130.jpg  sdc10165.jpg 
 Public             sdc10064.jpg  sdc10103.jpg  sdc10131.jpg  sdc10166.jpg 
 

 am I doing anything wrong any ideas/suggestions would be gratefull  
 

 Thank you

---

### Post by Elfy on 2009-10-17
You are forgetting case sensitivity - try changing to Desktop

---

### Post by triggerchar on 2009-10-17
Thank you very much for the quick reply this is sorted although i do feel stupid thank you

---

### Post by Elfy on 2009-10-17
There are no stupid questions ;)

I spent ages trying to find x11 instead of X11 ...

---

### Post by Paqman on 2009-10-17
Also, a good shortcut: ~ is your home folder. And don't forget tab autocompletes things.

So to get to your desktop, you could just type ```
~/De*[tab]*
```

---

### Post by MrWES on 2009-10-17
> **Paqman said:**
> Also, a good shortcut: ~ is your home folder. And don't forget tab autocompletes things.

So to get to your desktop, you could just type ```
~/De*[tab]*
```

Also, if you have directories you cd to on a regular basis, you could setup an alias (.bash_aliases) to help out.

```
alias gomovies='cd /media/external/Movies'

```

So now I just type gomovies and the terminal will cd into /media/external/Movies for me. Neat stuff.

---

