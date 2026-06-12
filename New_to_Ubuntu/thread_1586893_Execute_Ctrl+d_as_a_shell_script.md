---
title: "Execute Ctrl+d as a shell script"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by jhaveri.hiral on 2010-10-02
Hello,
I want to execute Ctrl+d in my shell script. 

Actually I have done "chroot" in a shell scipt file..

Now I am running another script file from the changed root..
**From this shell script I need to go back to original root by using shell script only..**
So I need to execute Ctrl+d via shell script..

I have tried following scripts after reading few forums on it:--

1] echo -e "\0004"
2] perl -e "print \"\\x1A\";" | blah_command_to_recieve_it

but these does not work.. 
the second command with some modification -->
3] perl -e "print \"\\x1A\";"

this also does not work .. it simply prints some symbol..

I also tries "exit" but it simply comes out of the program and not from the changed root..

Plz give useful guidance..
Thank you..

---

### Post by apmcd47 on 2010-10-02
Firstly you don't execute Ctrl-D in a shell-script - you don't execute Ctrl-D period. When the terminal process receives a Ctrl-D it knows an end-of-file has been reached. Normally to emoulate the end-of-file in a shellscript, or a perlscript, a HERE-DOC is used, e.g.
```
function usage() {
cat << EOT
Usage: $0 [options] [args]
where ....
....
....
EOT
}
```
But what exactly are you doing? You want to chroot another script but from within that script you want to remove the chroot? I'm sure chroot won't allow that. Or are you running a subshell within the script, in which case when the subshell comes to an end, so does the chroot?

Andrew

---

### Post by jhaveri.hiral on 2010-10-02
I am firstly starting my system from the live USB.
Then I am executing file with following commands in file "rec" :- 
```

sudo mount /dev/sda7 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
#now control is transfered to changed root
#after exit from their, following lines are executed
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/usr
sudo umount /mnt

```

Then when chroot transfers control to the mounted device, there I execute following script in file "rec1"
```

update-grub
grub-install /dev/sda
sudo grub-install --recheck /dev/sda
exit

```

Here instead of exit, I want Ctrl+d to be executed so that I can go back to the first script i.e "rec" to complete remaining umount commands.

Guide 4 the same..
Thank you...

---

### Post by sisco311 on 2010-10-02
Instead of starting a shell with chroot, run the second script directly:
```
chroot /mnt /path/to/second/script
```

Or run the second script in the current shell:
```
. /path/to/second/script
```

---

