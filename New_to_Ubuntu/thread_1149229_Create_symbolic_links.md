---
title: "Create symbolic links?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by allenbradley on 2009-05-05
I have a matlab starting script stored in /opt/matlab. I want it to be executed everytime I type matlab in the terminal. How do I set it up? ( I did not get the option during installation ). Is this called a symbolic link? ( I have been googling it for a while and getting results different from what I expected )

---

### Post by lavinog on 2009-05-05
if you type ```
echo $PATH
```
you will see a colon seperated list of paths that are checked when you enter a filename
generally you need a script located in one of these paths
here is my path list:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
I would put your script in /usr/local/bin
you can symbolically link the script to that location
```
sudo ln -s /opt/matlab/scriptname /usr/local/bin/scriptname

```
Also have you tried Octave
It works pretty good for a Matlab replacement.

---

### Post by tjwoosta on 2009-05-05
try 

```
ln -s /opt/matlab /bin/matlab
```

or 

```
ln -s /opt/matlab /usr/local/bin/matlab
```

(All this does is create a symbolic link for the file matlab in the directory /usr/local/bin (or /bin))

After this you should be able to just run the command matlab and it will automatically search for the file in either the /bin or /usr/local/bin directory depending on what you prefer (it will find the symlink and execute /opt/matlab)


EDIT: damn, just a moment too late

and yes i forgot you need to use sudo because the directories require root privelages to write

---

### Post by lavinog on 2009-05-05
Also if you ever need to find where your symbolic link is located, or the location of any executable
```
whereis scriptname
```
it will show you the full pathname of the file that will be executed if it is located in your path setting.

---

### Post by allenbradley on 2009-05-05
Thank you lavinog and tjwoosta! Got matlab up and running.

@lavinog : I do have octave, but my department professors refuse to deal with anything but matlab. Hopefully, that attitude changes in the near future.

Also, this may seem silly, is the thanks feature removed?

---

### Post by tjwoosta on 2009-05-05
yep, they removed it a while back because of all the server issues

---

### Post by lavinog on 2009-05-05
> **allenbradley said:**
> Thank you lavinog and tjwoosta! Got matlab up and running.

@lavinog : I do have octave, but my department professors refuse to deal with anything but matlab. Hopefully, that attitude changes in the near future.

I understand, but the matlab scripts should work just the same in octave (with exception to recently added features.
I just used octave for my final project instead of excel (recommended by the professor), boy that turned out to be interesting. End result, excel 07 has some really nice surface graphs. Openoffice has no such feature. My octave plots though were unique from everyone else's.


> 
Also, this may seem silly, is the thanks feature removed?
yes, it was causing some performance issues on the server

---

### Post by allenbradley on 2009-05-05
@lavinog maybe my guide does deserve a surprise once in a while.. Thanks for the tip!

---

### Post by lethalfang on 2009-05-05
Octave is promising, but I have some scripts that don't run on Octave. Maybe I could get it working if I try harder, but I haven't had the time yet.

---

### Post by allenbradley on 2009-05-05
Well, all the best for that. Do post when you manage to convert all your scripts!

---

