---
title: "install a program"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by tropnevad on 2009-04-10
i have a program that is in the form of a .sh format.. how do i go about installing this?  Can i install this on ubuntu?

---

### Post by cariboo on 2009-04-10
You can install the program, but what is the name of the program as it my be in the repositories, and you can use Add/Remove Programs or Sysnaptic Package Manager to install it. If you have to install the .sh program, the first thing you have to do is make it executable. Open a Applications-->Accessories-->Terminal and type:

```
sudo chmod +x ~/*sh
```

the above command assumes that the file is on the desktop and is the only file with an .sh extension. To run the program in the same terminal change directories to the desktop:

```
cd ~/Desktop
```

now that you are in the Destop directory run the file:

```
./*sh
```

Again the above command assumes the there is only one .sh file on your desktop. If you have more than one .sh file you will have to type the full filename eg:

```
./scan_all.sh
``` 

Jim

---

### Post by jakupl on 2009-04-10
you can also do it through GUI. right click the file, go to "permissions" and tick "allow executing file as program". now you can click the file and click "run".

---

