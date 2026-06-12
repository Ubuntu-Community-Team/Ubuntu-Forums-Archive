---
title: "what do the different colors for files mean?"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-22
hi
When I do a ls of a directory, I see all the files displayed in different colours. Is there somewhere to go to learn what the different colours mean?
 For example, when I do a ls of /bin some files are light green, 
some magneto, some are in a red block, etc.

I have Ubuntu 10.10 with ( I think ) the default bash shell.

---

### Post by spaik on 2010-12-22
[http://manpages.ubuntu.com/manpages/hardy/man5/dir_colors.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/dir_colors.5.html)
[http://ubuntuforums.org/showthread.php?t=501914](http://ubuntuforums.org/showthread.php?t=501914)


hope you find what you are looking for :)

---

### Post by karthick87 on 2010-12-22
Blue color - Directory
 Green color - Executable or recognized data file
 Sky Blue Color - Linked file
 yellow with black background - device
 Pink colour - graphic image file
 Red - Archive file

 **For your Information:**
 If you don't like them, you can turn them off in **.bashrc** 
 To turn the color of you have to comment out the following lines in **.bashrc**.
[IMG]http://i.imgur.com/NqbiF.png[/IMG] 
Also if you want to see your own bash color meanings,then copy/paste the following codes in your terminal.
```
eval $(echo "no:global default;fi:normal file;di:directory;ln:symbolic link;pi:named pipe;so:socket;do:door;bd:block device;cd:character device;or:orphan symlink;mi:missing file;su:set uid;sg:set gid;tw:sticky other writable;ow:other writable;st:sticky;ex:executable;"|sed -e 's/:/="/g; s/\;/"\n/g') 
{      
IFS=:     
for i in $LS_COLORS     
do        
echo -e "\e[${i#*=}m$( x=${i%=*}; [ "${!x}" ] && echo "${!x}" || echo "$x" )\e[m" 
done       
} 
```[B]
Output:[/B]
[IMG]http://i.imgur.com/nfbKg.png[/IMG]
 **Note:**
For more informations type **man dir_colors** in terminal.

---

### Post by s1baker on 2010-12-22
thanks. this will be solved now.

---

