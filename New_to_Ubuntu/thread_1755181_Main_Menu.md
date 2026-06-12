---
title: "Main Menu"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by rosswmcgee on 2011-05-10
I wish to create an icon for Seamonkey which I was able to install to be compatible with Natty. It now works but I need and Icon. Here is the read me
instruction that I can not seem to figure out. Where is the panel menu?

 To hook up SeaMonkey complete with icon to the GNOME Panel,
  follow these steps:

  1. Click the GNOME Main Menu button, open the Panel menu, and then open
     the Add to Panel submenu and choose Launcher.

  2. Right-click the icon for SeaMonkey on the Panel and enter the
     following command:

       directory_name./seamonkey

     where directory_name is the name of the directory you downloaded
     SeaMonkey to. For example, the default directory that SeaMonkey
     suggests is /usr/local/seamonkey.

  3. Type in a name for the icon, and type in a comment if you wish.

  4. Click the icon button and type in the following as the icon's location:

       directory_name/chrome/icons/default/default.png

     where directory_name is the directory where you installed SeaMonkey.
     For example, the default directory is
     /usr/local/seamonkey/chrome/icons/default/default.png.

---

### Post by dcsoldschool53 on 2011-05-10
On the attachment, you will see a picture of a screw on the launcher. Click the screw icon on your system's launcher. navigate to /usr/local/seamonkey/chrome/icons/default/default.png, or where you install seamonkey.. This is where you will find the icon for seamonkey. Click on the one that you want.

In ubuntu 10.10 right click gnome panel > add to panel > customize applications launcher to get to the launcher.

On the Applications menu, right click Applications > Edit Menus. Click on the folder where you want to place seamonkey. Click new item to get to a launcher.. I know that you are in natty but I was hoping it worked the same way.

---

### Post by rosswmcgee on 2011-05-11
This how I installed SeaMonkey 2.0.14, which is not in the synaptic manager. I downloaded into /home/ross/seamonkey. I can follow the path as you instructed but I still find no icon, and no ability to launch. Head a little fuzzy after trying everything. here is the path result.
Failed to execute child process "/home/ross/seamonkey/seamonkey/chrome/icons/default/default.png" (Permission denied)



Installation Instructions
-------------------------------

  Note: There is no installer available, but just extracting the tar.bz2
  to the default directory (usually /usr/local/seamonkey) achieves the
  same result as an installer would.

  To install SeaMonkey by downloading the tar.bz2 file:

  1. Create a directory named "seamonkey" (mkdir seamonkey) and change
     to that directory (cd seamonkey).

  2. Click the link on the site you're downloading SeaMonkey from to
     download the package (seamonkey*.tar.bz2) file into the seamonkey
     directory.

  3. Change to the seamonkey directory (cd seamonkey) and decompress the
     file with the following command:

       tar jxvf sea*.tar.bz2

     This creates a "seamonkey" directory under your seamonkey directory.

  4. Change to the seamonkey directory (cd seamonkey).

  5. Run SeaMonkey with the following run script:

    ./seamonkey


Also when I do a file search Seamonkey 2.0.14 is not shown just 2.0.13. It is too bad that Ubuntu did not put the correct Seamonkey in the repositories, because you can not run the Seamonkey Browswer suite with out a crash, they are not compatible.

---

### Post by dcsoldschool53 on 2011-05-12
> **rosswmcgee said:**
> I wish to create an icon for Seamonkey which I was able to install to be compatible with Natty. It now works but I need and Icon. Here is the read me
instruction that I can not seem to figure out. Where is the panel menu?

 To hook up SeaMonkey complete with icon to the GNOME Panel,
  follow these steps:

  1. Click the GNOME Main Menu button, open the Panel menu, and then open
     the Add to Panel submenu and choose Launcher.

  2. Right-click the icon for SeaMonkey on the Panel and enter the
     following command:

       directory_name./seamonkey

     where directory_name is the name of the directory you downloaded
     SeaMonkey to. For example, the default directory that SeaMonkey
     suggests is /usr/local/seamonkey.

  3. Type in a name for the icon, and type in a comment if you wish.

  4. Click the icon button and type in the following as the icon's location:

       directory_name/chrome/icons/default/default.png

     where directory_name is the directory where you installed SeaMonkey.
     For example, the default directory is
     /usr/local/seamonkey/chrome/icons/default/default.png.

This is the way that I had installed Seamonkey on my system when I had downloaded the file.

1.) In a terminal ```
cd /usr/local
```2.) Copy the file to the usr local directory, and type in password```
sudo cp ~/Downloads/seamonkey-2.0.14.tar.bz2 /usr/local
```3.) Untar file, and you may need to type in your password```
sudo tar jxvf seamonkey-2.*.tar.bz2
``` (This will unzip the file and, create a seamonkey folder in your /usr/local directory.) 

4.) Change into the seamonkey directory ```
cd seamonkey
```5.) In the terminal run the following script:  ```
./seamonkey
```To get a icon for Seamonkey

1.)In ubuntu 10.10 right click gnome panel > add to panel > customize applications launcher to get to the launcher.
2.) When the launcher opened, I click on the picture of the screw to navigate to```
/usr/local/seamonkey/chrome/icons/default/
```3.)In this directory, I had to choose which .png file that I had wanted to use.
4.) Fill in the rest of the information

Type: Application
Command: /usr/local/seamonkey/seamonkey
Comment: Web browser

No, I did not follow their instructions to the letter, but it still works! Look at the files that I uploaded.

---

### Post by dcsoldschool53 on 2011-05-12
Creating a launcher for Seamonkey in Applications menu on your gnome panel.

1.) In the terminal, type```
alacarte
```2.) When it opens, scroll down the left side in Menus and click on Internet. 
3.) Look for New Item with a plus sign in front of it on the right. When you click on New Item, It will open up the launcher.
4.) Add you information and icon here.
5.) Click close

Good luck

---

### Post by rosswmcgee on 2011-05-12
I will get to work on this. Thanks

Ok I followed the directions to a tee, but this does not work in Natty 11.04 , if I were in 10.10 the seamonkey ion synaptic would work. If you are in Natty look at the applications in the software manger for seamonkey and read the review. 

So the only thing different doing it this way is the path, so I removed seamonkey 2.0.14 and re-installed it in the same 

path you used same result. I can run seamonkey from terminal in Natty 11.04, but cannot get a launcher or launcher with icon to open seamonkey. following the path all the way to default icons, in that folder I selected default.png


also no new app with a + sign is visible in the main menu. 

I tried another icon and got the usual msg.

Failed to execute child process "/usr/local/seamonkey/chrome/icons/default/seamonkey.png" (Permission denied)

There may not be a way, to fix this unless Ubuntu decides to upgrade the repository to 2.0.14 seamonkey.



I really appreciate your help with this, ubuntu is a learning process and we are in this together.

---

### Post by dcsoldschool53 on 2011-05-13
> **rosswmcgee said:**
> I will get to work on this. Thanks

Ok I followed the directions to a tee, but this does not work in Natty 11.04 , if I were in 10.10 the seamonkey ion synaptic would work. If you are in Natty look at the applications in the software manger for seamonkey and read the review. 

So the only thing different doing it this way is the path, so I removed seamonkey 2.0.14 and re-installed it in the same 

path you used same result. I can run seamonkey from terminal in Natty 11.04, but cannot get a launcher or launcher with icon to open seamonkey. following the path all the way to default icons, in that folder I selected default.png


also no new app with a + sign is visible in the main menu. 

I tried another icon and got the usual msg.

Failed to execute child process "/usr/local/seamonkey/chrome/icons/default/seamonkey.png" (Permission denied)

There may not be a way, to fix this unless Ubuntu decides to upgrade the repository to 2.0.14 seamonkey.



I really appreciate your help with this, ubuntu is a learning process and we are in this together.

Try this trick```
cd /usr/local/seamonkey/chrome/icons/default
```When you are in the default folder, type```
ls -l
```I think that we may need to change the .png's permission.
Use the chmod command to allow all users to use the .png icon.:D If you can not do it in that folder, copy the icons to Desktop and try it there.

---

### Post by rosswmcgee on 2011-05-13
Here is the read out. I cannot change permissions in the folder, but can on the desktop but it still does not open seamonkey just the icon image. I am not sure how to use chmod comand, I just changed permissions to read and write in all sections and checked the allow excute file as a program.

ross@ross-ET1161-05:~$ cd /usr/local/chrome/icons/default
bash: cd: /usr/local/chrome/icons/default: No such file or directory
ross@ross-ET1161-05:~$ cd /usr/local/seamonkey/chrome/icons/default
ross@ross-ET1161-05:/usr/local/seamonkey/chrome/icons/default$ ls -l
total 208
-rw-r--r-- 1 root root   866 2011-04-21 00:25 abcardWindow16.png
-rw-r--r-- 1 root root  3010 2011-04-21 00:25 abcardWindow48.png
-rw-r--r-- 1 root root  1885 2011-04-21 00:25 abcardWindow.png
-rw-r--r-- 1 root root   880 2011-04-21 00:25 ablistWindow16.png
-rw-r--r-- 1 root root  2689 2011-04-21 00:25 ablistWindow48.png
-rw-r--r-- 1 root root  1865 2011-04-21 00:25 ablistWindow.png
-rw-r--r-- 1 root root   846 2011-04-21 00:25 addressbookWindow16.png
-rw-r--r-- 1 root root  2657 2011-04-21 00:25 addressbookWindow48.png
-rw-r--r-- 1 root root  1724 2011-04-21 00:25 addressbookWindow.png
-rw-r--r-- 1 root root   838 2011-04-21 00:25 bmPropsWindow16.png
-rw-r--r-- 1 root root  3236 2011-04-21 00:25 bmPropsWindow48.png
-rw-r--r-- 1 root root  2104 2011-04-21 00:25 bmPropsWindow.png
-rw-r--r-- 1 root root   848 2011-04-21 00:25 bookmark-window16.png
-rw-r--r-- 1 root root  2728 2011-04-21 00:25 bookmark-window48.png
-rw-r--r-- 1 root root  1849 2011-04-21 00:25 bookmark-window.png
-rw-r--r-- 1 root root   862 2011-04-21 00:25 default16.png
-rw-r--r-- 1 root root  3429 2011-04-21 00:25 default48.png
-rw-r--r-- 1 root root  2015 2011-04-21 00:25 default.png
-rw-r--r-- 1 root root   851 2011-04-21 00:25 downloadManager16.png
-rw-r--r-- 1 root root  2525 2011-04-21 00:25 downloadManager48.png
-rw-r--r-- 1 root root  1649 2011-04-21 00:25 downloadManager.png
-rw-r--r-- 1 root root   877 2011-04-21 00:25 editorWindow16.png
-rw-r--r-- 1 root root  3180 2011-04-21 00:25 editorWindow48.png
-rw-r--r-- 1 root root  2018 2011-04-21 00:25 editorWindow.png
-rw-r--r-- 1 root root   935 2011-04-21 00:25 findBookmarkWindow16.png
-rw-r--r-- 1 root root  3305 2011-04-21 00:25 findBookmarkWindow48.png
-rw-r--r-- 1 root root  2135 2011-04-21 00:25 findBookmarkWindow.png
-rw-r--r-- 1 root root   912 2011-04-21 00:25 findHistoryWindow16.png
-rw-r--r-- 1 root root  3378 2011-04-21 00:25 findHistoryWindow48.png
-rw-r--r-- 1 root root  2083 2011-04-21 00:25 findHistoryWindow.png
-rw-r--r-- 1 root root   906 2011-04-21 00:25 history-window16.png
-rw-r--r-- 1 root root  3454 2011-04-21 00:25 history-window48.png
-rw-r--r-- 1 root root  2070 2011-04-21 00:25 history-window.png
-rw-r--r-- 1 root root   906 2011-04-21 00:25 JSConsoleWindow16.png
-rw-r--r-- 1 root root  3103 2011-04-21 00:25 JSConsoleWindow48.png
-rw-r--r-- 1 root root  1951 2011-04-21 00:25 JSConsoleWindow.png
-rw-r--r-- 1 root root   862 2011-04-21 00:25 main-window16.png
-rw-r--r-- 1 root root  3429 2011-04-21 00:25 main-window48.png
-rw-r--r-- 1 root root  2015 2011-04-21 00:25 main-window.png
-rw-r--r-- 1 root root   880 2011-04-21 00:25 messengerWindow16.png
-rw-r--r-- 1 root root  3207 2011-04-21 00:25 messengerWindow48.png
-rw-r--r-- 1 root root  1958 2011-04-21 00:25 messengerWindow.png
-rw-r--r-- 1 root root   858 2011-04-21 00:25 msgcomposeWindow16.png
-rw-r--r-- 1 root root  2947 2011-04-21 00:25 msgcomposeWindow48.png
-rw-r--r-- 1 root root  1825 2011-04-21 00:25 msgcomposeWindow.png
-rw-r--r-- 1 root root 12796 2011-04-21 00:25 seamonkey.png
-rw-r--r-- 1 root root   859 2011-04-21 00:25 venkman-window16.png
-rw-r--r-- 1 root root  3071 2011-04-21 00:25 venkman-window48.png
-rw-r--r-- 1 root root  1933 2011-04-21 00:25 venkman-window.png
ross@ross-ET1161-05:/usr/local/seamonkey/chrome/icons/default$

---

### Post by jtarin on 2011-05-13
I dowload icons to my /home/usr/.icons. Then travel there when I want a special one-off icon.

---

### Post by dcsoldschool53 on 2011-05-13
That is what it was suppose to do, open with an image program, because we have not connected the icon to Seamonkey yet. Remember we have to open up a launcher to connect the icon with Seamonkey's application. 
Now, when you had opened the image, did you get an error message along with. If not lets try to connect the icons from Desktop to Seamonkey.

1.) Let create a new folder and call it icons```
mkdir ~/Desktop/Icons
```If you don't want to create the folder to Desktop, create it in Pictures in your home folder.

2.) Move your Seamonkey's Desktop icons to their new home```
mv ~/Desktop/*.png ~/Desktop/Icons
```3.) Now, we need to create a launcher. Right click on Desktop. In the list, look for Create Launcher, and click on it.
4.) Click on the picture of the screw, and navigate to```
/home/your-user-name/Desktop/Icons/Select-your-icon-image.png
``` Which icon do you want to associate with Seamonkey.

5.) Name:```
Seamonkey
```6.)Command:```
/usr/local/seamonkey/seamonkey
```7.) Comments: Type whatever you want.

Now click OK. There should actually be a new seamonkey app on desktop. Click it to see if seamonkey opens.

---

### Post by dcsoldschool53 on 2011-05-13
> **jtarin said:**
> I dowload icons to my /home/usr/.icons. Then travel there when I want a special one-off icon.

This is a good idea, google some Seamonkey icons,and place them in a folder. Use them when you need them.

---

### Post by rosswmcgee on 2011-05-13
Seamonkey now opens, but I have a black square on the desktop instead of the icon.

Wow hard to believe. So all I have to do is perhaps re work this process to actually get the icon, but icon or not I now have a seamonkeybird iconlauncher. Thanks so much. I bet I may be the only person  running seamonkey 2.0.14 with natty 11.04
that has a  Seamonkey icon launcher. lol!!

It all started because I wanted an alternative to Opera 11.10 because with Opera there was one little applet I could not
get to work. What a journey.

Bottom line I know of no better linux os forum than Ubuntu, just great!!

---

