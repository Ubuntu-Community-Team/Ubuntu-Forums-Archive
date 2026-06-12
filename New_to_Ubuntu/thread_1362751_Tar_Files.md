---
title: "Tar Files"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by bobanshirl on 2009-12-23
I have downloaded a small game xye that I used to play in Windows it is in my Downloads Folder with a copy of it on my desktop.The problem I have is that it is a tar file,xye-0.9.1.tar.gz,and I dont know what to do next.I have searched the forums and the two Ubuntu books that I have,but am at a loss.Any help would be appreciated.I downloaded it from the linux section in Softpedia.com.

---

### Post by cariboo on 2009-12-23
Just double click the file and extract it to where ever you want. Once extracted, make sure you read any readme's and installation instructions.

---

### Post by itsbrad212 on 2009-12-23
or from Terminal:
```
tar xvf file.tar.gz
```

---

### Post by swoody on 2009-12-23
Cariboo nailed it here. Simply double-click, or right-click and select 'Extract' on the package. This will let you extract the contents of the file onto your computer. You can also use the terminal by:
Changing to the proper directory:
```
cd /home/username/Downloads/
```
Then extracting the package:
```
tar -xvf xye-0.9.1.tar.gz
```

Now you should see a file in the 'Downloads' folder named xye-0.9.1 which contains all of the extracted files.

---

### Post by vexorian on 2009-12-23
If you are a newbie wanting to install a tar.gz package, my advice is: don't. I would try linking to a .deb package instead, but this time I can't - It is unfortunate playdeb hasn't added xye to karmic's repository yet.


Anyway, you have two chances: install WINE and then run the windows version which runs fine. OR: install the tar.gz file.

To continue swoody's advice. You need to install these packages:
libsdl1.2-dev
libsdl-image1.2-dev
libsdl-ttf2.0-dev
checkinstall

Use synaptic to install them , then do (after following swoody's advice):

```

cd /home/username/Downloads/xye-0.9.1
./configure
make
sudo checkinstall

```
(input your password then follow the instructions, do not bother modifying descriptions or anything.

This will add a package xye that you will be able to uninstall using synaptic. I think though that it won't add an icon, you will have to type 'xye' manually  in a terminal to play the game. You may create a launcher manually by using the menu editor that is somewhere in preferences.

---

### Post by bobanshirl on 2009-12-24
Many thanks Vexorian, I took your advice and as I had Wine installed I thought I would see if it worked.I put the Computer Buyer floppy in.mounted the drive and after a few double clicks I had Kye(Xye) up and running,you obviously know your Ubuntu.Bob

---

