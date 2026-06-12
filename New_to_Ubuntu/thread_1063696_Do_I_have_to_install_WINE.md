---
title: "Do I have to install WINE?"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-08
Do I have to install wine to run a .exe file? And do I have to install Wine to run a DOS/Windows .exe Program?

---

### Post by gjoellee on 2009-02-08
You don't have to install WINE, there are other windows emulators as well. I recommend WINE though.

---

### Post by taurus on 2009-02-08
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by houstonbofh on 2009-02-08
You have to install something...  WINE, DosBox, WEMU, VMware...  Pick the one you like.

---

### Post by HermanAB on 2009-02-08
The best one is Crossover by Codeweavers.  (it is basically the bleeding edge of Wine).

Cheers,

Herman

---

### Post by taurus on 2009-02-08
> **HermanAB said:**
> The best one is Crossover by Codeweavers.  (it is basically the bleeding edge of Wine).

Cheers,

Herman

But it's not free (30-day free trial only).

---

### Post by Tek-E on 2009-02-08
Not necessarily wine if you dont want to. But some form of windows/DOS emulation software is required to run an .exe file. Linux (Ubuntu) alone cannot interpret and run an executable file.  There is next to nothing when it comes to compatibility with the majority of files that come from windows. So yes. Wine or some other emulation softwarel.  I personnaly reccomend wine.  But then again you might want to give crossover a try as well

---

### Post by eriqjaffe on 2009-02-08
Be aware that there is no guarantee that your program will run in Wine, as it's certainly not bulletproof.

Installing Windows in a virtual machine (VirtualBox, qemu, VMWare) will allow you to run the program in a "native" environment, although none of those solutions will help if your application requires 3D acceleration.

You can check Wine's App DB to see if other people have had any success or failure with whatever you're trying to run.

---

### Post by txcrackers on 2009-02-08
> **HermanAB said:**
> The best one is Crossover by Codeweavers.  (it is basically the bleeding edge of Wine).

It is **not** the "bleeding edge" - it's a highly stabilised version with GUI tools on top to manage it. The "bleeding edge" can be had from the code repository and/or via the WineHQ repository.

---

### Post by blazemore on 2009-02-08
TO GET THE UBUNTU STABLE RELEASE OF WINE

```
sudo apt-get install wine
```


TO GET THE MOST RECENT STABLE OFFICIAL VERSION OF WINE

1. ```
sudo su
```
This means that all commands run from now on will be run as the Super User (root), until you close the terminal window.


2.```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add
```
We download (wget) something called a "key" that verifies downloaded installation files. We install it. (apt-key add)


3. ```
echo deb http://wine.budgetdedicated.com/apt intrepid main >> /etc/apt/sources.list
```
echo just means display the next bit. The >> means append to the file /etc/apt/sources.list, which is a list of locations your computer uses to get software, when you ask it to.
In this case, we're using the official Wine repository, which has a more up-to-date version of Wine than the included Ubuntu repository.
We could just download the installation file from the Wine website, but the method I chose ensures Wine will be kept up-to-date.


4. ```
apt-get update
```
We refresh the list of repositories, making your computer aware of any new or updated packages


5. ```
apt-get install wine -y --force-yes
```
We install the package Wine (If it's not already installed). When the installer asks a question, we assume the answer is yes, even if yes is not the default option (You'll just have to trust me on this one!).


6. ```
apt-get upgrade -y --force-yes
```
If Wine was already installed, this command will update it to the version in the Wine repo, again, assuming Yes to all questions.

---

