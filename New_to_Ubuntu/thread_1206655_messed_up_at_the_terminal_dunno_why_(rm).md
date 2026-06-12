---
title: "messed up at the terminal dunno why (rm)"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by andyzammy on 2009-07-07
i wanted to transfer some pics from one folder into another, and i hastily stuck a cp and rm command anded together. my bad for being impatient and not doing one line at a time.

from what i could tell it should have worked but it didn't.

could someone please tell me what i did wrong?

```
~/Pictures/messabout$ cp *.jpeg /home/rofl/Pictures/DownThemAll/ && rm *.jpeg
```

i understood this line to copy all .jpegs from the messabout folder to the DownThemAll folder and delete them from the messabout folder. they weren't there though.

any help is appreciated.

---

### Post by OzzmanNT on 2009-07-07
I repeated the exact same process on my machine and the files were there. Kinda odd.

here is what I did to duplicate your scenario:

```
ozzmannt@ozzmannt-laptop:~/Desktop$ mkdir test1
ozzmannt@ozzmannt-laptop:~/Desktop$ mkdir test2
ozzmannt@ozzmannt-laptop:~/Desktop$ cd test1
ozzmannt@ozzmannt-laptop:~/Desktop/test1$ touch test.jpeg
ozzmannt@ozzmannt-laptop:~/Desktop/test1$ cp *.jpeg ../test2/ && rm *.jpeg
ozzmannt@ozzmannt-laptop:~/Desktop/test1$ ls
ozzmannt@ozzmannt-laptop:~/Desktop/test1$ cd ../test2
ozzmannt@ozzmannt-laptop:~/Desktop/test2$ ls
test.jpeg

```

I see no difference between what you did and what I did. Files** should **be in the DownThemAll directory.

---

### Post by Paddy Landau on 2009-07-07
Without seeing the error message, it's impossible to say.

Two ideas are that you might have had a typo; or, if rofl isn't you, then you might not have had permission to write to that directory.

Do you remember the error message?

---

### Post by andyzammy on 2009-07-07
there was no error message, and there was no typo, that was copied straight of the terminal. unfortunately the only other things i copied from the terminal were the ls of "messabout" before and after i put that command in, which only confirms that the jpegs were deleted from the folder i didn't want them in.

i went to the DownThemAll folder and no ."jpeg"'s in there at all. there are some ".jpg"'s that were already in there but i can't see that making any sort of difference.

does it matter that i'm using a screenlet terminal? sometimes there's a dodgey delay when i enter a command and what should show up, it takes a few more enters to display properly.

i repeated the command in two test folders on the desktop and worked perfectly. oh well, a one-off occurence hopefully.

thanks for your help guys! least i know i did it right.

---

### Post by Ratscallion on 2009-07-07
I suggest using a proper terminal (gnome-terminal???) and then maybe checking the trash. Something might have happened in the process to make them go in there.

---

### Post by iver2435 on 2009-07-07
Essentially what you're trying to do is a "move" operation, so why not just use:

```
mv *.jpeg /home/rofl/Pictures/DownThemAll/
```

Maybe you'll have better luck that way.  And I agree with Ratscallion about using gnome-terminal or some other "full-fledged" terminal.  The screenlet terminal may or may not be the issue, but why take a chance?

---

### Post by andyzammy on 2009-07-08
thanks for the suggestions!

Ratscallion i thought using (any) terminal rm command immediately perm-deletes from the computer? are you saying that gnome-terminal has a recycle bin?

and yep, mv is deffo next on my list of commands to learn. i'm trying to learn what i need to do through the shell. i already knew how to copy and delete so thought i could achieve moving using a combo of the 2. guess not :P

mv it is then!

---

### Post by lisati on 2009-07-08
I agree with iver2435 that often mv is often easier and safer. My own preference is to do the cp (or equivalent) first and make sure the files end up where you want them, before doing the rm - there's less chance of losing stuff that way.

---

### Post by Ratscallion on 2009-07-08
Haven't got much experience in the old rm, if it was moved to the trash, it would be your own... Not the Terminal's.

---

### Post by Paddy Landau on 2009-07-08
When you use *rm*, the file is gone. There's no wastebasket.

If you use *mv* to move a file on the same filesystem, then *mv* simply moves the file's entry to the new directory; the physical file stays put. Thus, it's extremely fast and efficient in that case.

You might also want to learn about linking. Start with the *ln* command. Search Google or these forums to learn the difference between a *hard link*, a *relative soft link*, and an *absolute soft link*. (An absolute soft link is the equivalent of a shortcut in Windows.)

---

### Post by Ratscallion on 2009-07-09
Ah, thanks!

---

