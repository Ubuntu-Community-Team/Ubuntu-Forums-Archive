---
title: "Can't get the XP operating system working only ubuntu"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by danielseyfried on 2009-05-17
I tryed yesterday to get this working by downloading a boot info script
to my desk top and typing in the terminal sudo bash -/Desktop/boot_info_script*.sh and I should of gotten something called RESULTS.text but instead I got thisubuntu@ubuntu:~$ sudo bash -/Desktop/boot_info_script*.sh
bash: -/: invalid option
Usage:	bash [GNU long option] [option] ...
	bash [GNU long option] [option] script-file ...
GNU long options:
	--debug
	--debugger
	--dump-po-strings
	--dump-strings
	--help
	--init-file
	--login
	--noediting
	--noprofile
	--norc
	--posix
	--protected
	--rcfile
	--restricted
	--verbose
	--version
	--wordexp
Shell options:
	-irsD or -c command or -O shopt_option		(invocation only)
	-abefhkmnptuvxBCHP or -o option
ubuntu@ubuntu:~$ 

I've redone this about four times and it always comes out the same, could someone tell me what I am doing wrong?

    Thanks

---

### Post by mapes12 on 2009-05-17
Looks like your script hasn't executed because -/ Desktop is not a valid option. The options are then listed out.

It would be helpful if you could explain how you installed Ubu i.e. inside windoze, dual boot or whatever. If windoze was on your machine ahead of Ubu then Grub should have installed to handle a dual boot configuration. Also, how did you configure your partitions for Ubu? Post the output to  ```
sudo fdisk -l
```

---

### Post by blackened on 2009-05-17
The hyphen preceeding the path should be a tilde, which would be a shorthand way of pointing to your home directory (/home/*username*/Desktop is the same as ~/Desktop)
```
sudo bash **-**/Desktop/boot_info_script*.sh
```

should be

```
sudo bash **~**/Desktop/boot_info_script*.sh
```

---

### Post by danielseyfried on 2009-05-17
Windows was installed before Ubuntu and both are on the same drive.
When the computer starts up a black screen comes up with Ubuntu downloads
at the top and Windows below that with other operating systems at below that.I configured the particions in XP before I loaded Ubuntu.I haven't any major problems with Ubuntu since I installed it which was about a year
ago.This problem might of been caused when I tryed to down load Thunderbird which I did Yesterday.

          Thanks

---

