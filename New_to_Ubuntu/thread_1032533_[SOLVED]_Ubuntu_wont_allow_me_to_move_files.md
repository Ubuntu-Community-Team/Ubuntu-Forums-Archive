---
title: "[SOLVED] Ubuntu wont allow me to move files"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by concerto on 2009-01-06
Hey guys.  I need some help.

I had some files on "computer A" that I wanted to move to "computer B".  Both computers are running Ubuntu.

I burned all files from "computer A" to a disk and put them on "computer B".

Now Ubuntu will not let me move files and their are pictures of little locks on the upper right of my icons?

How do I get rid of the little locks so I can move my files where I want them? 

Thank you for your time.

---

### Post by mapes12 on 2009-01-06
The little locks mean you do not have permission to move them. A quick fix is to move them as super user by launching nautilus like this. In Terminal: ```
gksudo nautilus
```If you have the 2 Ubu boxes connected on a network there is a much easier solution to move files from one machine to another using ssh. Post back if you need the HowTo on this.

---

### Post by concerto on 2009-01-06
I'm new to all this stuff mapes12.  Isn't their an easier way to take the locks off?

---

### Post by mapes12 on 2009-01-06
Nope!

Did you run the command?

Permissions are there to make your system safe.

---

### Post by concerto on 2009-01-06
root@concerto:/home/concerto# gksudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:9017): WARNING **: Unable to add monitor: Operation not supported

---

### Post by concerto on 2009-01-06
I got it!  I ran the command and a program opened up called "Desktop File Browser".  I moved all the files in the program and the locks went away.  now what do i do?  It wont let me take the files back out?!?!

---

### Post by Therion on 2009-01-06
I'm not sure what you mean by "take the files back out".  

You've used Nautilus (the default file browser in Ubuntu) to copy the files from the CD you burned to the hard drive on Computer B.  The little padlock icons are gone from the files since you've use "sudo" to copy them and now you should have full read/write access to those files.  

What is it you're trying to do with these files now and how are you trying to do it?

---

### Post by concerto on 2009-01-06
When I typed the command "gksudo nautilus"  a window opened up on my desktop called File Browser.  I dragged all the files with locks on them into it and the locks disappeared but now I cant get the files out of file browser.  :(

---

### Post by concerto on 2009-01-06
It looks like I copied all of my files to the Root file browser all i need to know is how to get them back.

---

### Post by Therion on 2009-01-06
You seem to be a little confused about what Nautilus is.  Nautilus (the file browser) is a file managing tool only, it's not a destination.  You've COPIED your files USING the File Manager Nautilus using Root privileges to do so. 

The files do not reside IN Nautilus, they now reside on the hard drive.

Now, do you want to move these files again, to some OTHER location on your hard drive?

---

### Post by theinnercityhippy on 2009-01-06
> **concerto said:**
> I'm new to all this stuff mapes12.  Isn't their an easier way to take the locks off?

If you want to change the permission s for any file so that you can open/write to it as a normal user follow these instructions. First open a terminal

Accessories > Terminal

This will open a window with a command prompt (a shell).

Type into it this

$> sudo chown [your username] [file name you want to change]

For the filename I find it is best to be in that directory to do this as it avoids confusion. For instance, to move to the folder "Documents" in your home folder, type 

$> cd Documents

{note all file names are case sensitive and it is best to avoid using spaces in filenames}

Anyway, going back to the first command, you will be prompted for your password, enter it and you should now own that folder. To change the permissions for all of the files in a folder use this command

$> sudo chown -R [your username] [folder name you want to change]

The -R you typed tells the command to act recursively, ie to all files within.

Hope this helps you

-JimDog*-

---

### Post by concerto on 2009-01-06
Ok.  because of everyones help I have everything figured out.  some things just came up and i have to run.  thank you everyone!!!!!!  thread solved!!!!!!!!!

---

### Post by concerto on 2009-01-06
The main problem that I was having was that I was logged in as root but I still had to go into properties and change the permissions to "read and write" instead of just read only.  I'm good now.  Thank you again everyone!!!!!

---

