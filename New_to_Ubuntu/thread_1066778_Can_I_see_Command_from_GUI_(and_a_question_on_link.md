---
title: "Can I see Command from GUI? (and a question on links)"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Andavane on 2009-02-11
In my continuing efforts to make familiarity with the terminal (and I am using a guide), I wondered if it were possible to make an action with GUI, and see what the command for that would be. Perhaps that way it might feel more intuitive.

Is that possible?

And the question on links:

If I make a folder, which is linked in one folder to another folder, and I decide that I want the link folder to become the main folder, is it possible to do that?

Regards

John

---

### Post by taseedorf on 2009-02-13
well, one could make a gui program to tell you what each command could do...but they don't need that. It'd be pointless.  type <command> --help to find out information about the command.

so for example
sudo --help might give you some information
iwconfig --help
etc...


As for your second question, a link cannot be a main folder.  What I am understanding is not making sense.  A link to a folder is just that. you could, but you would have to move the folder. thats all.

---

### Post by mikechant on 2009-02-13
> I wondered if it were possible to make an action with GUI, and see what the command for that would be.

The answer is "it depends". Simplifying, a gui application can perform actions in three ways.
 
It can invoke operating system/library functions - in which case no command line tool is involved, and there may not be a direct command line equivalent as such (e.g. an OS call to open/close files). 

It can also perform actions internally (e.g. using its own code, crop an image held in memory). Again, no command line tool is involved. 

Or, it can invoke one or more command line tools to perform various functions.

An example of a gui application that invokes command line tools is the 'Grip' CD ripper. This by default invokes such command line tools as 'cdparanoia' to perform the ripping and 'lame' to do mp3 encoding. 

The actual tools it uses are user definable; the options passed can be seen and changed; and the output from these commands, along with the actual command and all its options, are visible in the gui status log tab when executed. I suggest installing and playing with this application (it's a good, useful app anyhow, and not likely to screw anything up) to see what I mean.

The apps I mention (grip, lame, cdparanoia) are all in the Ubuntu repositories - lame might be in one of the repositories you have to activate (?universe) but you've probably already done that.

---

