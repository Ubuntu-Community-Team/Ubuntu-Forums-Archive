---
title: "How do I use &quot;su&quot; in terminal to copy a file into a directory?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by Kike89 on 2010-03-03
Im trying to install a facebook plug-in in mozilla, but I get restrictions when trying to copy the file into the mozilla plugin directory. I know that I have to do it in a terminal window as a root using "su" but after researching in the internet I haven't found how to do it; the only thing I know to do is to open the terminal, write su, hit enter, enter pass, and that's it... I don't know the commands to copy the file and paste it in the firefox plugin's directory. I want to learn how.

Thx

---

### Post by diablo75 on 2010-03-03
```
sudo -s
```

That will make the rest of the terminal session function as the super user.  Just be careful, you could really F your system up if you fat finger a command.  ;)

---

### Post by bodhi.zazen on 2010-03-03
> **Kike89 said:**
> Im trying to install a facebook plug-in in mozilla, but I get restrictions when trying to copy the file into the mozilla plugin directory. I know that I have to do it in a terminal window as a root using "su" but after researching in the internet I haven't found how to do it; the only thing I know to do is to open the terminal, write su, hit enter, enter pass, and that's it... I don't know the commands to copy the file and paste it in the firefox plugin's directory. I want to learn how.

Thx

Ubuntu uses sudo

sudo cp foo /destination

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Kike89 on 2010-03-03
> **diablo75 said:**
> ```
sudo -s
```That will make the rest of the terminal session function as the super user.  Just be careful, you could really F your system up if you fat finger a command.  ;)

enrique@enrique-laptop:~$ sudo -s
[sudo] password for enrique: 
root@enrique-laptop:~# 

-----------------------------------------
thx,

now what should I do?

---

### Post by sisco311 on 2010-03-03
> **Kike89 said:**
> enrique@enrique-laptop:~$ sudo -s
[sudo] password for enrique: 
root@enrique-laptop:~# 

-----------------------------------------
thx,

now what should I do?

Press Ctrl+d to exit from the root shell.


Then type:
```
sudo cp
```
type a space, drag the file in the terminal window to get the full path to it, type another space, drag the destination directory in the terminal & press Enter. Type in your password & press Enter again.

---

### Post by Kike89 on 2010-03-03
> **bodhi.zazen said:**
> Ubuntu uses sudo

sudo cp foo /destination

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

sorry but I still don't get it. I want to copy this file /home/enrique/Desktop/libnpfbook_1_0_3.so   and paste it here /usr/lib/firefox/plugins

---

### Post by sisco311 on 2010-03-03
> **Kike89 said:**
> sorry but I still don't get it. I want to copy this file /home/enrique/Desktop/libnpfbook_1_0_3.so   and paste it here /usr/lib/firefox/plugins

```
sudo cp /home/enrique/Desktop/libnpfbook_1_0_3.so /usr/lib/firefox/plugins
```;)

---

### Post by diablo75 on 2010-03-03
> **Kike89 said:**
> enrique@enrique-laptop:~$ sudo -s
[sudo] password for enrique: 
root@enrique-laptop:~# 

-----------------------------------------
thx,

now what should I do?

You can use the cp command to copy files.  The syntax is basically:

```
cp [/source/location/filename] [/destination/folder]
```

Something you could do alternatively is run an instance of nautilus as root so you can right-click on the file you want to copy, hit copy, then browse to where you need to put it and right-click>paste it.  If you're at a root prompt, you could just type "nautilus" and it'll fire up a new window as root (and only that window, every other window is still your own account so you can't drag and drop between windows unless you fire an additional instance up).

You could also run "gksudo nautilus" from any terminal to run a fresh instance as root.

---

### Post by Kike89 on 2010-03-03
[QUOTE=diablo75;8911634]You can use the cp command to copy files.  The syntax is basically:

```
cp [/source/location/filename] [/destination/folder]
```

That was easy, I feel dumb :P thx.

---

### Post by QIII on 2010-03-03
By way of a little explanation, in order of the commands you are seeing everyone suggest.

sudo -- elevate my privileges (any time you issue this for the first time in a session, you will be prompted for your password.  Type it in.  But you won't see anything in the terminal.  That is normal.)

cp -- copy.  Use cp, because if something weird happens, you will still have the original copy in the current place.  mv (move) literally moves the file out of the original location and puts it in a new location.  Use mv sparingly for now.

foo -- the name of the file you want to move.  Assuming it is in your /home partition, you will not need to qualify it further.  When you open the terminal, you are in your /home partition by default.

/destination -- where you want to put the file.  You generally have to do something like /destination/subdestination/subsubdestination.

---

### Post by bodhi.zazen on 2010-03-03
> **diablo75 said:**
> ```
sudo -s
```That will make the rest of the terminal session function as the super user.  Just be careful, you could really F your system up if you fat finger a command.  ;)

sudo -s works, but

```
sudo -i
``` is preferred.

See :

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by Kike89 on 2010-03-03
I did it but it stills not working, is this where I should install firefox plug ins? /usr/lib/firefox/plugins

---

### Post by galdren on 2010-03-03
I'm wondering...isn't there a GUI way to install this firefox plugin like you install most of the FF plugins?

If not then try to find some kind of readme or howto about installing this plugin..maybe there are some other steps needed

---

### Post by bodhi.zazen on 2010-03-03
> **Kike89 said:**
> I did it but it stills not working, is this where I should install firefox plug ins? /usr/lib/firefox/plugins

What is not working exactly ?

What command did you run ? What error message are you getting ? Did you re-start firefox?

In general one can install plugins into ~/.mozilla/firefox/

the home directory ;)

Use /usr/lib/firefox for all users.

On my system I see

/usr/lib/firefox-addons/plugins, perhaps you need to use that directory ?

---

### Post by Kike89 on 2010-03-03
> **bodhi.zazen said:**
> What is not working exactly ?

What command did you run ? What error message are you getting ? Did you re-start firefox?

In general one can install plugins into ~/.mozilla/firefox/

the home directory ;)

Use /usr/lib/firefox for all users.

On my system I see

/usr/lib/firefox-addons/plugins, perhaps you need to use that directory ?

I just pasted the file there, I'm supossed to be able to upload pictures but I can't, I don't get any error message, just a facebook message telling me that I have to install the plug-in which I have already installed. When I Dclick the file it says this "There is no application installed for shared library files" but anyways, it's a library I don't think it's necesary to open it.

Thx for your help

edit: maybe I did something wrong from the beggining, is there a way to uninstall firefox, install it, and try to install the plug-in from scratch?

---

### Post by bodhi.zazen on 2010-03-03
Hmm ...

Did you re-start firefox ?

Clear your cache ?

cookies ?

Are you blocking javascript ?

Sorry, I am not familiar with the add on, what is it exactly ? Is there a home page ?

---

### Post by Kike89 on 2010-03-03
> **bodhi.zazen said:**
> Hmm ...

Did you re-start firefox ?

Clear your cache ?

cookies ?

Are you blocking javascript ?

Sorry, I am not familiar with the add on, what is it exactly ? Is there a home page ?

when I try to upload a picture I just get prompted with a window that says that I need to install an add-on (mac style), I click download and that's all. I will try clearing my cache and cookies.

---

### Post by bodhi.zazen on 2010-03-03
did you re-start firefox ?

---

### Post by hansheijmans on 2010-03-03
There is also the possibility of using a graphical user interface with root permissions for those who are not comfortable with command line.

Press Alt+F2 (Run application window). Then type:

```
gksudo nautilus
```This will bring up the File Browser with root permissions.

As mentioned by everyone else: be careful!!!! Close this window immediately when done.

---

### Post by Kike89 on 2010-03-03
> **bodhi.zazen said:**
> did you re-start firefox ?

I did restart it.

Naitilus doesn't work for me, dont know why, when I try to do something in the root graphical window, it says that I dont have permission.

---

### Post by J V on 2010-03-03
oh ffs, just give him gksudo nautilus and let him do it the easy way :)

---

