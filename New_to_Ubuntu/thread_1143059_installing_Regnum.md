---
title: "installing Regnum"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by tsuchang on 2009-04-29
I downloaded the Regnum game to my desktop.  I have instructions to:
"Once it's downloaded, open a terminal on your Linux OS, go to the directory which your install file is in, and type in the following, exactly at it is shown here:

chmod a+x name_of_file.bin (Press Enter)


sudo ./name_of_file.bin (Press Enter)

Replace "name_of_file" with the name of your Regnum install file. Executing these two commands should cause the Regnum installer to run, and install the game on your computer."

I can figure out how to do some of that but the beginning part has me baffled.
I can open the terminal so perhaps I'm not completely waisted but how do I go to the directory?  As I said above it is on the desktop.

Thanks

Oh yeah.  I know not to type in the, (press enter) hehehe

---

### Post by didiercool on 2009-04-29
If it's on your desktop, type in > chmod a+x /home/YOU_USER_NAME/Desktop/REGNUM_FOLDER_NAME/NAME_OF_FILE.bin

and then,

> sudo /home/YOU_USER_NAME/Desktop/REGNUM_FOLDER_NAME/NAME_OF_FILE.bin

Any time you see ~/something or ./something, it usually means you put in /home/username/wherever the file is/ etc.

And you type all of that into the terminal.

Also, you will probably need a 'sudo' before 'chmod'

---

