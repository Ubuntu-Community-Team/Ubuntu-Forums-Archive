---
title: "OOWeb or Kompozer"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by muddpup64 on 2010-11-10
I want a web designing program for my 10.10 Ubuntu and I was wondering which is better OOWeb or Kompozer? Is there something better? How do I install it?

Thanks

---

### Post by qamelian on 2010-11-10
They have two separate purposes. Kompozer is for designing websites, and OOWeb is an HTTP server.

---

### Post by alphacrucis2 on 2010-11-10
Kompozer is ok but needs work. From what I can tell the dev is off doing other things at present so I don't know whether or not there will be much progress. You may want to keep an eye on [Bluegriffon]("http://www.bluegriffon.org/") which is under active development and looks promising. It's some way from a stable release though. As the other poster said OOWEb is for a different purpose.

---

### Post by theozzlives on 2010-11-10
I use Front Page 2003. One the reasons I still have a Windows 7 box.

---

### Post by ayenack on 2010-11-10
Bluefish is my personal favourite.

**sudo apt-get install bluefish**

---

### Post by qamelian on 2010-11-10
> **ayenack said:**
> Bluefish is my personal favourite.

**sudo apt-get install bluefish**

I second Bluefish. It's my favourite app on any OS for coding websites.

---

### Post by muddpup64 on 2010-11-10
I just downloaded BlueGriffon, how do I install?

---

### Post by shankhs on 2010-11-11
> **muddpup64 said:**
> I just downloaded BlueGriffon, how do I install?

I assume its a tar.gz file so you just untar it using 

tar -xvz <filename>

cd to the new directory and find if there is any install script , if there is none try
./configure
make
sudo make install

There may be many unresolved dependencies which you might have to manually download and install.

I haven't checkd it but if you face any problem just put a quick reply here.

---

### Post by muddpup64 on 2010-11-11
You've lost me.

---

### Post by Jetso on 2010-11-11
Okay, 
1.) Drag file to desktop for ease. 
2.) Start Terminal Applications>Accesories> Terminal
3.)```
cd Desktop
```
4.) tar xvf <*file name*>
5.) If there is a .sh file double click that file, and choose "Run in Terminal"
6.)If not ```
./configure
```
```
ake
```
```
sudo make install
```

After that, it's installed :P

---

### Post by themusicalduck on 2010-11-11
> **muddpup64 said:**
> I just downloaded BlueGriffon, how do I install?

I just downloaded the folder. It's a pre-compiled binary, so you just need to click on the file called "blugriffon".

---

### Post by muddpup64 on 2010-11-11
I understand it up to the tar xvf <*filename*>.

---

### Post by themusicalduck on 2010-11-11
Download the file to your desktop.

Find the file, right click it and select Extract Here. Then look inside the extracted folder and look for the file named "bluegriffon". Click that file and it should just start the program.

If you want to install it as it were, then you'll need to save the folder somewhere and then make your own menu entry and browse to the same bluegriffon file that you start it with.

---

### Post by muddpup64 on 2010-11-11
> If you want to install it as it were, then you'll need to save the  folder somewhere and then make your own menu entry and browse to the  same bluegriffon file that you start it with.

What?

---

### Post by themusicalduck on 2010-11-11
> **muddpup64 said:**
> What?

The program runs if you click that file right?

If you want it hidden away and there to be a menu launcher, like if it were installed.. then you'll need to copy the folder to somewhere (like your home folder), then right click on the menu in the top left, click Edit Menu, click to add a new entry under one of the sub-menus, then put in the name you want for the entry, click browse and find the file that launches the program according to where you copied it to.

It's not necessary to run it, just good if you plan to use the software frequently.

---

### Post by llamabr on 2010-11-11
seamonkey comes with a reasonably good editor.

---

### Post by muddpup64 on 2010-11-11
Thats so cool, I didn't even know you could edit your menu, but thanks a lot.:guitar:

---

