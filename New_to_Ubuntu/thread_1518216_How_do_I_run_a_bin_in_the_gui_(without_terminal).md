---
title: "How do I run a bin in the gui (without terminal)"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by odielag on 2010-06-26
I downloaded planeshift, and now have a .bin in the downloads folder. I would hate, hate, to use the terminal even though the concept seems easy enough. I went into the bin's properties using the gui and set it to be allowed to execute, and I have read and write ability as this user. 

So, how do I execute a .bin file in the gui (without using terminal at all).

PS: I searched dozens of results having to do with running bin files, have yet to see an answer to my question.

Thanks, and I'm really enjoying ubuntu so far. I'm also hoping the games I'm downloading with wine:steam will work. (crosses fingers)

---

### Post by Penguin Guy on 2010-06-26
Make sure it has execute permissions, then just double click it. If that nothing happens then it's probably the program's fault.

---

### Post by odielag on 2010-06-26
TY for the quick response.

In properties under permission it says it's able to execute (I checked it earlier).

On right click it gives me the option to open, which gives this error "Could not display "/home/myname/Downloads/PlaneShift-v0.5.4-x64.bin"."

and there also is the option to open it with "Other Application"s.

Any ideas?

---

### Post by mk1w86 on 2010-06-26
I know you don't want to use the terminal but it will probably be much easier if you do, I find the GUI handling of files like this can be awkward.  You could try selecting the terminal under the Other Applications option otherwise if you run the following commands you should be able to install the game:

```
cd /home/myname/Downloads/
```

This will change to the Downloads directory where the bin file is.  Then run:

```
sudo ./PlaneShift-v0.5.4-x64.bin
```

to actually execute the file as root (sudo means execute the command as root) which should then launch its installer as long as the correct permissions are set. ;)

---

### Post by odielag on 2010-06-26
I right clicked to open it with another program, and was hoping to find the terminal as an option. Terminal was not in the list of options.

I am still looking for a way to run the .bin program without having to use the terminal and type.

---

### Post by gandaran on 2010-06-26
> **odielag said:**
> I right clicked to open it with another program, and was hoping to find the terminal as an option. Terminal was not in the list of options.

I am still looking for a way to run the .bin program without having to use the terminal and type.
I doubt there is one! but you can still make things easier by installing *nautilus-open-terminal* ( need reboot to work) then right click the file or folder, choose open in terminal and just type the run command.

---

### Post by Dr_Willis on 2010-06-26
it is a good idea to state exactly what 'bin' file you are trying to run.
Theres such variation in them that its hard to offer good suggestions other then to actually learn/try it in the terminal.

I say this because there ARE .bin 'installers' that are command line only, so they need to be ran in a Xterm, or via the console. 

The terminal is our friend. :lolflag:

---

### Post by odielag on 2010-06-30
I tried installing the *nautilus-open-terminal* using the ubuntu software center, then I rebooted. I see no menu option to open the program in a terminal when looking at the planeshift .bin file in a regular folder.

Original question: How do I run a .bin program without opening the terminal and typing in the name of the program.

---

### Post by oldos2er on 2010-06-30
Don't right-click on the *.bin file, right-click on an empty spot in the folder.

I don't really understand the terminal-phobia. You could've had this installed days ago and saved yourself some grief.

---

### Post by eriktheblu on 2010-06-30
Why not just create a launcher?

---

### Post by steveneddy on 2010-06-30
You can't copy and paste? Really?

All of the commands are on the forums page of the software you downloaded:

[http://www.hydlaaplaza.com/smf/index.php?PHPSESSID=bcabd44f1906cc6c9affad17dfa1c557&topic=31776.0](http://www.hydlaaplaza.com/smf/index.php?PHPSESSID=bcabd44f1906cc6c9affad17dfa1c557&topic=31776.0)

simply highlight the words or phrase you want to copy - that is it - just highlight it - press no buttons or make any other mouse gestures.

Now open up a terminal and either middle click the mouse - on the scroll wheel - or if using a laptop tap two fingers in the touch pad and it will paste whatever you just highlighted.

It's so easy even some Windows users and gamers can figure it out.

:lolflag:

---

### Post by steveneddy on 2010-06-30
> **eriktheblu said:**
> Why not just create a launcher?

The .bin file is a launcher - but the user must use the correct commands for it to operate properly.

If a person is going to use Linux then they may as well get used to the terminal.

---

### Post by gandaran on 2010-07-04
> **odielag said:**
> I tried installing the *nautilus-open-terminal* using the ubuntu software center, then I rebooted. I see no menu option to open the program in a terminal when looking at the planeshift .bin file in a regular folder.

Original question: How do I run a .bin program without opening the terminal and typing in the name of the program.
what you open is the folder containing the bin file from the drop-down menu 'open in terminal' option then type the run command
* sudo sh name of file.bin*
there is no other way to run the bin file without the terminal.

---

