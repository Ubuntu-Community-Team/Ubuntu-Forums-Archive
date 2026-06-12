---
title: "boot Ubuntu"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by moehoffman on 2011-07-14
I am running Ubuntu with XP. Yesterday I ran a Ubuntu update. Today, when I try Ubuntu, I get a 
grub>     prompt. What can I do to start Ubuntu?  thx

---

### Post by moehoffman on 2011-07-14
thank you

---

### Post by Blasphemist on 2011-07-14
Please see this from here. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
> GRUB 2 Troubleshooting Preparation
In order to successfully boot from the "grub>" prompt, the user should locate/verify the:

Partitions - The / partition, and any separate partitions such as a boot partition.
Files - Location of the linux and initrd.img files (normally in /boot) and the grub.cfg file in /boot/grub
The following commands will help determine this information.

set
When set is typed without additional entries the command displays the current GRUB 2 settings.
ls
The Linux partition should be listed, as should any special partition such as a separate boot or home. Example: (hd0) (hd0,1) (hd1,5) In this example sda, sda1, sdb5 are recognized. For (hd1,5), the X value is 1 and the Y value is 5.
ls (hdX,Y)/
This result should include vmlinuz and initrd.img
ls (hdX,Y)/boot
This result should include the specific kernel and initrd.img files
ls (hdX,Y)/boot/grub
Included should be numerous *.mod files and the grub.cfg file, as well as various *.img files.
**''grub>'' Prompt Booting**
If GRUB 2 leaves you at the grub> prompt, it has normally found the grub folder and loaded at least some basic modules. The configuration file (grub.cfg) may be missing or corrupted.

If the user has confirmed the paths and existence of the proper folders in the previous section, attempt to load the configuration file with the following command:
configfile (hdX,Y)/boot/grub/grub.cfg
If the configuration file is located, the GRUB 2 menu should appear and the user should be able to choose a selection and boot. If the configuration file is not found, a message will be generated and the user must enter the boot commands manually.
Press ENTER after completing each line. Some entries will not provide feedback. This is normal.
If a "file not found" or similar error message is displayed while running these commands, ensure you are using the correct X,Y values.
Command Summary *:
set root=(hdX,Y)
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img
boot
Expanded Instructions *:
1.* set root=(hdX,Y)
Type with correct X,Y results confirmed earlier and press ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. Example: If the Ubuntu system is on sda5, enter: set root=(hd0,5)
2.* linux /vmlinuz root=/dev/sdXY ro
Example: linux /vmlinuz root=/dev/sda5 ro
* Wubi users see note.
3. initrd /initrd.img
Selects the latest initrd image.
4. boot
Boot to the latest kernel on the selected partition.
* Wubi users only - substitute these commands in Steps 1 and 2:
set root=(loop0)
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
Remember that the commands issued at the grub. prompt are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now correctly point to the correct locations. The user may need to reinstall GRUB 2 (sudo grub-install /dev/sdX).
If the system fails to boot, proceed to the grub rescue> section to run more targeted boot commands.
Rescue Mode (''grub rescue>'') Booting
The GRUB 2 rescue mode is a major enhancement to the GRUB bootloader. The presence of the grub rescue> prompt signifies that GRUB 2 has failed to find the grub folder, the grub.cfg file, and the associated modules. The rescue prompt is presented so the user can provide the path to the grub folder, load the necessary modules, and provide the proper boot commands.

A common reason for the grub rescue> prompt is an incorrect path to the grub folder. Reasons for the prompt could include a failure to update GRUB 2 after certain system or partition operations, improper designation of the grub folder location, or a failed installation.

To successfully boot from the grub rescue> prompt:

The grub folder must exist and contain the necessary GRUB 2 files.
The proper path must be set via the set prefix command.
Many GRUB 2 commands will not work until the correct path is set.
If the path to the grub folder (normally /boot/grub) is not correct, an unknown command or file not found message is likely.
The necessary modules must be loaded.
The kernel cannot be loaded until the 'linux' module is loaded.
A Linux kernel and initrd.img must be located and loaded.
Use the GRUB 2 Troubleshooting Preparation section to locate the correct partitions and file locations. The following commands are available in the Rescue mode.

The rescue mode provides fewer commands than the normal GRUB prompt line, but also provides these additional commands:

Command
Result
dump
Clears memory
exit
Exit GRUB 2
normal
Return to the standard "grub>" mode if possible.
Among the commands which can be used in the grub rescue mode if the normal module can be loaded:
boot
cat
chain
help
insmod
linux
ls
multiboot
normal
search
set
unset
Once the user has confirmed the paths and existence of the proper folders in the previous section, run the following commands:
Rescue Prompt Boot Instructions (* Wubi Users See Note):
1. set prefix=(hdX,Y)/boot/grub
Use the values determined earlier. Example: If the Ubuntu system is on sda5, enter: set prefix=(hd0,5)/boot/grub
2.* set root=(hdX,Y)
Example: set root=(hd0,5)
3. insmod normal
Attempt to load the normal module.
4. normal
Activate the normal module. If successful, the GRUB 2 menu may appear.
5. set
(Optional) Review the current settings.
6. ls /boot
(Optional) Check for a vmlinuz and a initrd.img entry.
7. insmod linux
An error message usually means the path is incorrect.
8.* linux /vmlinuz root=/dev/sdXY ro
Selects the latest kernel. Example: linux /vmlinuz root=/dev/sda5 ro
9. initrd /initrd.img
Selects the latest initrd image.
10. boot
* For Wubi installs (within Windows) only substitute these commands in Steps 2 and 8:
2. set root=(loop0)
8. linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
Some additional considerations:
The current prefix and root settings may be checked at any time with the set command. To remove a setting, use the unset command (example: unset prefix).
Modules must be loaded before they can be used. If a module has not been loaded a unknown command error is displayed. If an incorrect path is specified, a file not found error message may be displayed.
The linux module must be loaded to be able to load both the kernel and the initrd image unless the normal module is loaded first.
If the modules cannot be found in the /boot/grub folder, the user may be able to load them from the /usr/lib/grub/i386-pc folder. The address if Ubuntu was installed on sda1 would be (hd0,1)/usr/lib/grub/i386-pc and the command would be: insmod (hd0,1)/usr/lib/grub/i386-pc/normal.mod
For a successful boot from the rescue prompt, the prefix path and root= setting must be correct, the linux module must be loaded, and the kernel (vmlinuz) and initrd image (initrd.img) must be accepted.
 The user should attempt to load the normal module to regain more capabilities while in the Grub 2 terminal. Try loading the normal GRUB 2 module with insmod normal, followed by normal on a separate line to activate the module. If successfully loaded and activated, help and additional commands will be available.
These changes are not permanent. After successfully booting into the system the user should run sudo update-grub and inspect the GRUB 2 configuration file (/boot//grub/grub.cfg). For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the [### BEGIN /etc/grub.d/10_linux ###] section of the file now point to the correct locations. The user may need to reinstall GRUB 2 using sudo grub-install /dev/sdX.
Boot a Specific Kernel Manually
If a GRUB 2 menu is not available for editing during the boot process the command line may still allow booting a specific kernel. If GRUB 2 is looking in the correct location a user may be able to enter all the necessary information on the command line in a single entry. This section will provide a step-by-step guide on how to enter this information. The line will look similar to the following when completed:

Command Summary *:
set
linux /boot/vmlinuz-<your version> root=/dev/sdXY ro
initrd /boot/initrd-<your version>
boot
Expanded Instructions *:
Press ENTER only after completing each step ("1", "2", "3" and "4").
Step 1*. Set the Root Partition
set root=(hdX,Y)
Use the correct X,Y results from the ls command and ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. For example, if the Ubuntu system is on sda5, enter: set root=(hd0,5)
* For a Wubi install inside Windows, substitute the following command:
set root=(loop0)
Step 2*. Enter the "linux" line information
linux /boot/vmlinuz-<your version> root=/dev/sdXY ro
* For a Wubi install inside Windows, substitute the following command:
root=/dev/sdXY loop=/ubuntu/disks/root.disk
Afer typing linux /boot/, the user can TAB to display the available kernels. There is no space character after "/". If no kernels are visible, the address in the "Set Root" section may be incorrect. Enter the correct kernel by typing or using tab completion.
For the root=/dev/ section use the correct device such as "/dev/sda1", "/dev/sdb5", etc
Add any options, such as ro (read-only), at the end of the line (normally not required).
Once all the information on the line is correct it should look similar to the sample below.
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro
When correctly typed and ENTER, if the linux kernel is found, a line similar to the "Linux-bzImage" confirmation line highlighted below will appear.

If a "file not found" or similar error message occurs, either the device/partition/file does not exist or GRUB 2 is not looking at the correct drive, partition and/or directory. Determine the correct location using the ls command and then run the following command. Repeat Step 2.
set prefix=(hdX,Y)/boot/grub
Step 3. Enter the "initrd" line information
initrd /boot/initrd.img-<your version>
Afer typing initrd /boot/, the user can TAB to display the available initrd images. Do not leave a space after the "/". If no images are visible, the address in the "Set Root" section may be incorrect. Enter the correct image by typing or using tab completion.
Once all the information on the line is correct it should look similar to the sample below. Press ENTER. Look for confirmation.
initrd /boot/initrd-2.6.31-16-generic
When correctly typed and entered, if the initrd image is found, a line similar to the "Initrd"" confirmation line highlighted in the graphic above should appear.
Step 4. Boot
boot
Type the command and press ENTER.


---

### Post by idoitprone on 2011-07-14
> **moehoffman said:**
> thank you


thank who? lol

Are you running wubi?
here is the mega wubi thread
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

get live cd and type 
```
sudo fdisk -l
```
If you only have ntfs then you are running wubi

If you really want full conformation then
go to this link
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by amjjawad on 2011-07-14
> **moehoffman said:**
> I am running Ubuntu with XP. Yesterday I ran a Ubuntu update. Today, when I try Ubuntu, I get a 
grub>     prompt. What can I do to start Ubuntu?  thx

We can't just help you blindly, you need to provide more details.

---

