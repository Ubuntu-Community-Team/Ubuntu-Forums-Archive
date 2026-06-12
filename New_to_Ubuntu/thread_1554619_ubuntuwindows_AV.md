---
title: "ubuntu/windows AV"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by julianrdlph on 2010-08-17
i've been using ubuntu for a while now, and i love it.  im not sure if im posting this in the right place, but ima post anyway.

i was wondering if there is a distro, hopefully based on ubuntu, that i can run from a usb drive that is loaded with antivirus and anti spyware programs that i can use to scan a windows machine.

i found klamav and i can use it, but i havent figured out how to use it to scan windows.

this is what i did:  i made a ubuntu live usb, ran it on the windows machine, updated it, installed ntfs support, updated klamav...and then i tried to run it.  
i thought that maybe if i added ntfs support that klamav would be able to scan the windows...but it didnt.

so basically, what i want to know is if something like this exists.  if not, can someone please send me to a place where i can make "my own distro" that will do this.  like a step by step sort of thing, i dont and cant program (other than "hello world" if ya get what i mean)...

thanks a million!

---

### Post by anglican on 2010-08-17
> **julianrdlph said:**
> i've been using ubuntu for a while now, and i love it.  im not sure if im posting this in the right place, but ima post anyway.

i was wondering if there is a distro, hopefully based on ubuntu, that i can run from a usb drive that is loaded with antivirus and anti spyware programs that i can use to scan a windows machine.

i found klamav and i can use it, but i havent figured out how to use it to scan windows.

this is what i did:  i made a ubuntu live usb, ran it on the windows machine, updated it, installed ntfs support, updated klamav...and then i tried to run it.  
i thought that maybe if i added ntfs support that klamav would be able to scan the windows...but it didnt.

so basically, what i want to know is if something like this exists.  if not, can someone please send me to a place where i can make "my own distro" that will do this.  like a step by step sort of thing, i dont and cant program (other than "hello world" if ya get what i mean)...

thanks a million!Just use ubuntu, I'll leave you to find instructions for making a bootable USB (google will help you here). Once booted, open a terminal and type:

```
sudo apt-get install clamav
sudo freshclam
```which will install AV software. Then you need to find and mount your Windows disk:
```
sudo fdisk -l
```then depending on where your ntfs filesystem is found:
```
sudo mkdir /mnt/windows_disk
sudo mount /dev/xxxx /mnt/windows_disk -o ro
```where xxxx should be obvious from the output of the fdisk command. Finally to scan the disk type:
```
clamscan --bell -r --log=/home/yourname/virus_log -i /mnt/windows_disk/

```[COLOR=Black]The above command will scan your [/COLOR][FONT=courier new][COLOR=Black]/mnt/windows_disk/[/COLOR][/FONT][COLOR=Black] directory ([/COLOR][FONT=courier new][COLOR=Black]NTFS[/COLOR][/FONT][COLOR=Black] partition) recursively ([/COLOR][COLOR=Black][FONT=courier new]-r[/FONT]) and log ([/COLOR][COLOR=Black][FONT=courier new]--log[/FONT]) the result in the virus_log file, will beep ([/COLOR][COLOR=Black][FONT=courier new]--bell[/FONT]) each time a virus has been detected and only print ([/COLOR][COLOR=Black][FONT=courier new]-i[/FONT]) infected files to the output.
[/COLOR] 
H

---

### Post by bkratz on 2010-08-17
You might find something useful here

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch)

---

