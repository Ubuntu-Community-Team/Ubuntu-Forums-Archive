---
title: "search .exe files in a folder/drive"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by net-reg on 2009-03-03
Hi all,
      Can u please tell me how to search and list all *.exe files on my usb drive (say /media/usbdrive/ ) and erase them in one line bash command.
    
        I got my usb drive infected (yeah from wind..) :-)

       U might say why not run antivirus, but i am trying to learn linux also in this way.

       Thanks all.

---

### Post by Nxion on 2009-03-03
> **net-reg said:**
> Hi all,
      Can u please tell me how to search and list all *.exe files on my usb drive (say /media/usbdrive/ ) and erase them in one line bash command.
    
        I got my usb drive infected (yeah from wind..) :-)

       U might say why not run antivirus, but i am trying to learn linux also in this way.

       Thanks all.

I would say the safest way and easiest way to resolve this issue is to format and start over. Who knows what else is infected. not all infections can be from an EXE. is there data still needed on the pendrive?

---

### Post by net-reg on 2009-03-03
hmmm yes that is good suggestion. virus file can be in other types also.

but please answer my query also as this will help me in learning commands, ie, using find/grep. am at early stages of learning.

i can see virus files from ubuntu :-) . they are just sitting there waiting for win..

---

### Post by Nxion on 2009-03-03
I would still say the safest is to format and start over. But if you really wanted to...

Well one way to do it is first find the files:

```
sudo find /path/to/usb/drive -name '*.exe'
```

This command will find the files in the path you supply. So change [COLOR="Red"]"/path/to/usb/drive"[/COLOR] to the actual path where the files are.

To delete the files you can do this:

```
sudo rm -f /path/to/usb/drive/*.exe
```

I would also suggest you read [this]("https://help.ubuntu.com/community/DeletingFiles") and [this]("https://help.ubuntu.com/community/find"). It will give you a better understanding about these commands. The rm command is a very powerful and dangerous command. Use it wisely and carefully. and make double and triple sure you have the right path before you run the commands.

** REMEMBER IN BOTH COMMANDS TO CHANGE [COLOR="Red"]"/path/to/usb/drive"[/COLOR] TO THE ACTUAL PATH OF THE DRIVE WHERE YOU WANT TO REMOVE THE FILES.

---

### Post by net-reg on 2009-03-04
thanks indeed!!!

---

### Post by neanderthalman on 2009-03-04
I was cleaning up a recovered drive recently - the recovery software had duplicated and triplicated my files, so I had things like picture001.jpg picture001jpg_1.jpg cluttering up my folders.  Turns out that rm is not compatible with both the -R (recursive) option and wildcards at the same time. NXion's command **will not delete .exe files in subdirectories.**

I found this command [here](http://en.tuxero.com/2007/09/how-to-delete-useless-windows-files-in.html) and it worked out well for me.

You're looking to modify it like this.  
```
find /path/to/usb/drive -type f -name "*.exe" -exec ls -f {} \;
```

replacing /path/to/usb/drive with whatever your actual drive path is.

This will not delete your files, only list them for now (note the command at the end is ls, not rm).  This is a safety check, because you can really mess up your system with a recursive wildcard delete.

A list of your .exe files on your usb should scroll up through the screen, so take a look and make sure these are the files you want to delete.

Then, use the same command, only with rm in place of ls:

```
find /path/to/usb/drive -type f -name "*.exe" -exec rm -f {} \;
```

---

