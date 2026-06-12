---
title: "Help with a terminal problem (no pun intended)"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by chris.willis on 2009-06-20
So sorry about this - I have looked around but am confused.

I have Ubuntu on my laptop and use OpenOffice everywhere. I store all my files on a SDHC Card and when I used to use Windows, I had a batch file to copy the files from the card to the hard drive as a backup. The theory is I can just take out the card and use it at any of the computers. Works great for me. Anyhow, now that I use Ubuntu as my primary laptop, I would like to replicate this so I don't have to manually copy and paste stuff. So I therefore have three questions:

1. The batch file contains the Windows Dos command: copy /y j:\Personal\*.* C:\Personal so what is the Ubuntu equivalent, and

2. How do I create a file on my desktop which I double click to execute the command?

3. If I wanted to do subdirectories and all the files and folders in that subdirectory, what would the command be?

Any help will be great!
With thanks,
Chris

---

### Post by nandemonai on 2009-06-21
> **chris.willis said:**
> So sorry about this - I have looked around but am confused.

I have Ubuntu on my laptop and use OpenOffice everywhere. I store all my files on a SDHC Card and when I used to use Windows, I had a batch file to copy the files from the card to the hard drive as a backup. The theory is I can just take out the card and use it at any of the computers. Works great for me. Anyhow, now that I use Ubuntu as my primary laptop, I would like to replicate this so I don't have to manually copy and paste stuff. So I therefore have three questions:

1. The batch file contains the Windows Dos command: copy /y j:\Personal\*.* C:\Personal so what is the Ubuntu equivalent, and

2. How do I create a file on my desktop which I double click to execute the command?

3. If I wanted to do subdirectories and all the files and folders in that subdirectory, what would the command be?

Any help will be great!
With thanks,
Chris

A simple bash script will do it:

```
#!/bin/bash
cp -uvr /source/dir/* /destination/dir/
```

cp - copy
-u update
-v verbose
-r recursive

Save the script in a file, something like backup.sh then to invoke the script simply call it using it's full path. Something like:

```
/home/user/scripts/backup.sh
```

Depending on where you save the script of course ;)

To make an icon simply add a launcher to the panel or desktop and use the script location as the 'command' and make sure the type is set to application in terminal. That way you can verify it worked.

You can add a couple lines to the bottom of the script to confirm it worked, wait for you to press enter then exit the terminal.

```
echo "Press Enter to continue."
read
exit
```

echo "" - display test
read - pause and wait for user to press a key
exit - close the terminal

---

### Post by chris.willis on 2009-06-21
"To make an icon simply add a launcher to the panel or desktop and use the script location as the 'command' and make sure the type is set to application in terminal. That way you can verify it worked."

-- Not sure about this part. So I right click on the file, select 'Make Link' then move that link to the desktop -- and from there, I have a dim light bulb over my head! Sorry: I don't understand!!

---

### Post by chris.willis on 2009-06-21
Hang on - I think I'm getting somewhere. I right click on the desktop then click Create Launcher ... 

Ok, done that, chose the Backup.sh file gave it the name 'Backup', application in terminal and when double clicked, it says 'There was an error creating the child process for this terminal'.

---

### Post by biriachan on 2009-06-21
If you like you could simple leave the script you created on your desktop and double click it.

You will be given a few options: "Run in Terminal" (Opens a new Terminal and executes the script0, "Display" (Opens the Script as a Text File in Gedit), "Cancel", and "Run" (Executes script without a Terminal)

In order to execute the script you will need to give the script rights to be executable.

Right Click on the Script -> Properties. Click on the "Permissions" Tab.  Next ensure under "Execute:" The box is checked ("Allow Executing File as Program".


If you don't like to leave the script file siting on your desktop you can move it to any location and create a "link", "shortcut", or "Launcher" as it's also know.

To do so move the file to where you want to save it.  Right click on the "Panel Bar" Select "Add to Panel".  Select "Custom Application Launcher", then Click the "Add" button.

A new dialog box will open with three text fields.

"Name" - Displayed Name of Launcher

"Command" - This is where you will need to supply the absolute path, suchas "/home/<User Name>/Location/Script.sh

"Comment" - This is the text that will be display when hovering the mouse over the Launcher.

---

### Post by chris.willis on 2009-06-21
That's excellent: I used a combination of the two. Created my script in my  home directory, changed the property to allow executing file as program, created a launcher on my desktop. When I double click the original file, it asks my what to do. When I double click my launcher, it automatically uses the terminal. Great. That's what I wanted. All solved - thanks so much!

---

