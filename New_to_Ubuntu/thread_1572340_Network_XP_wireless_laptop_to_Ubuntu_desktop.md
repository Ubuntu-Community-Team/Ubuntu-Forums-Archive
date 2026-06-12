---
title: "Network XP wireless laptop to Ubuntu desktop"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by BMU1 on 2010-09-10
I've installed Ubuntu a couple of days ago and need some help/advice. Ubuntu is on my desktop and is connected using an Ethernet port to the gateway. I have a laptop running XP and connects wireless to the same gateway to the internet.

I want to connect to from the XP laptop to the Ubuntu desktop and play some media on the Ubuntu desktop and watch it on the laptop. I dont want to copy all files over as the laptop does not have a lot of space.

I did some research and came across this site: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html) is that the best option? and will connecting through my ip use up my Internet bandwidth? if no, will the video play normally or might it be choppy?

Appreciate if anyone could help or point me to some docs to get this done.

---

### Post by Nythain on 2010-09-11
samba... it will basically create a network share that windows can recognize, from there you can access/stream/copy/whatever depending on how you set it all up

---

### Post by seventhsamurai on 2010-09-11
Yes, install samba from Synaptic Package manager. Then create a folder on your Ubuntu machine, right click and go to Sharing Options. Click on Share this folder.

You're set. Browse the network from your windows machine and you should see the folder listed.

---

### Post by BMU1 on 2010-09-18
ok, so i've installed samba on ubuntu and set up a folder with sharing privilidges. I'm trying to set up a new network connection on xp. I entered \\xxx.xxx.x.xx\share_dir and  get a popup stating to enter the user. I enter the user id and password but it does not connect. It redisplays the popup and populates the user name box with name/myusername. I've tried the ubuntu user password as well as the samba user password and the results are the same. Any suggestions?

note: ubuntu has 2 users and samba and the samba user/pswd are both set up on user1 there.

---

### Post by sandyd on 2010-09-18
> **BMU1 said:**
> ok, so i've installed samba on ubuntu and set up a folder with sharing privilidges. I'm trying to set up a new network connection on xp. I entered \\xxx.xxx.x.xx\share_dir and  get a popup stating to enter the user. I enter the user id and password but it does not connect. It redisplays the popup and populates the user name box with name/myusername. I've tried the ubuntu user password as well as the samba user password and the results are the same. Any suggestions?

note: ubuntu has 2 users and samba and the samba user/pswd are both set up on user1 there.
```

sudo apt-get install system-config-samba
gksudo system-config-samba
```
start from there.

Set the server permissions to "share".

Its on the "options" or "prefrences" menu if memory serves correct.

---

### Post by BMU1 on 2010-09-18
> **sandyd said:**
> ```

sudo apt-get install system-config-samba
gksudo system-config-samba
```start from there.

Set the server permissions to "share".

Its on the "options" or "prefrences" menu if memory serves correct.

sudo apt-get install system-config-samba
says:
system-config-samba is already the newest version.

gksudo system-config-samba
shows a popup which shows a folder which is set to share (permissions:read/write & visibility:visible)

Not sure how to get to his folder from xp.:confused:

---

### Post by sandyd on 2010-09-18
> **BMU1 said:**
> sudo apt-get install system-config-samba
says:
system-config-samba is already the newest version.

gksudo system-config-samba
shows a popup which shows a folder which is set to share (permissions:read/write & visibility:visible)

Not sure how to get to his folder from xp.:confused:
can you list the menus (or show me a screenshot)?
Theres an option up there that you have to change to disable password authentication.

actually.
```

sudo nano /etc/samba/smb.conf
```press Ctrl + W and type in "security" without quotes.

Change it from "user" to "share"
without quotes.

Press Ctrl + X, then Y, then ENTER
Restart.

sorry about the restart part. Things function much differently in gentoo, and I don't know how to restart using the new method in ubuntu....

oh, and just go to \\xxx.xxx.x.xx instead of typing the full path

---

### Post by macem29 on 2010-09-18
you my have everything set up on the ubuntu server fine but just need to find the shares on the XP
notebook....to find shared networks try this: right click on the windows start button, select explore,
select network neighborhood, select entire network, select windows workgroup...if the server is
serving, you should see it there with whatever you named the ubuntu box when you set it up,
double click on it to see the shared folders...not sure about the naming of all that 'cause I don't have
an XP machne around right now, but try that process and see where you get

---

### Post by BMU1 on 2010-09-18
> **sandyd said:**
> actually.
```

sudo nano /etc/samba/smb.conf
```press Ctrl + W and type in "security" without quotes.

Change it from "user" to "share"
without quotes.

Press Ctrl + X, then Y, then ENTER
Restart.
Competed that.

> **sandyd said:**
> 
sorry about the restart part. Things function much differently in gentoo, and I don't know how to restart using the new method in ubuntu....

oh, and just go to \\xxx.xxx.x.xx instead of typing the full path
typing  \\xxx.xxx.x.xx when setting up a network place in xp gives"windows required a share to publish. please specify another location." Do i need a router? as mentioned in the original post I've only got a Internet gateway.

Besides How do i verify that the samba server is running? I cant find any indication and running /etc/init.d/samba start in the terminal gives: bash: /etc/init.d/samba: No such file or directory

Sorry for all the questions. New to Ubuntu.

---

### Post by BMU1 on 2010-09-18
> **macem29 said:**
> you my have everything set up on the ubuntu server fine but just need to find the shares on the XP
notebook....to find shared networks try this: right click on the windows start button, select explore,
select network neighborhood, select entire network, select windows workgroup...if the server is
serving, you should see it there with whatever you named the ubuntu box when you set it up,
double click on it to see the shared folders...not sure about the naming of all that 'cause I don't have
an XP machne around right now, but try that process and see where you get
So i drilled down to 'My Network Places > Entire Network > Microsoft Windows Network' In there i see a ntwork that i previously attempted to set up but no option of a connection to ubuntu.

I tried the network place wizard again and get the popup stating 'connecting to xxx.xxx.x.xx' with the titlebar of the popup saying 'connect to ubuntu.ubuntu-domain'. But i dont know what user passwork it requires as I've tried all combos of the ubuntu superadmin as well as general user/pswd as well as that of the samba user/pswd. But it simply keeps rediaplaying the pop asking for it again. The windows popsuggesdts 'username' 'username@domain' 'DOMAIN/username' Not sure what it needs :confused:

---

### Post by macem29 on 2010-09-18
hmmmm, just checked something here for chits and giggles, I'm at a friends house and have my ubuntu
netbook with me that I have setup for sharing at home with an XP desktop, so kinda the reverse of what you
have going...anyway there's a Vista box here and I was able to see my ubunbtu shared folders on it by
navigating that network place stuff (named a little differently on Vista) I was asked for username and pass,
entered the details for my ubuntu login and voila: visible folders...as for creating the shared folders on the
ubuntu machine it could not have been easier: right clicked on the folders I wanted to share, properties, selected the
sharing tab, clicked on share this folder and got a "you don't have the software currently installed for this"
message, click here to download and install, did what I was told and it just worked, found out later after
reading a bit was that what I did was install Samba, not saying this will work for you, but it is something to try

---

### Post by BMU1 on 2010-09-18
> **macem29 said:**
> ...anyway there's a Vista box here and I was able to see my ubunbtu shared folders on it by
navigating that network place stuff (named a little differently on Vista) I was asked for username and pass,
entered the details for my ubuntu login and voila: visible folders...
Which user/pass did you enter? I'm not asking for the actual details, what i mean is that i tried the ubuntu user + ubuntu pswd. I also tried the samba user (which is the same as the ubuntu user) + the samba pswd. But i cant get in. Seems that the network wizard is able to see the ubuntu machine via the ip but i cant figure out what user/pswd it wants.

> **macem29 said:**
> as for creating the shared folders on the
ubuntu machine it could not have been easier: right clicked on the folders I wanted to share, properties, selected the
sharing tab, clicked on share this folder and got a "you don't have the software currently installed for this"
message, click here to download and install, did what I was told and it just worked, found out later after
reading a bit was that what I did was install Samba, not saying this will work for you, but it is something to try
I'be already installed samba and set up sharing for a specific folder within the Home folder. Did you share the Home folder or a sub-folder?

I just restarted my computer and i cant seem to start samba under 'system > administration > smaba' anymore. I get the wait-clock and then it disappears and nothing happens. Earlier i was able to open it and view the folders that had been shared. ggrrr..

---

### Post by macem29 on 2010-09-18
in the vista machine when prompted I enterd the only ubuntu pass I have, the one I used when installing
the OS...

I've successfully shared the homefolder, usb drives and SD media...the method I ended up using to get Samba installed did not require the entering of any passwords...do the folders your trying to share have
the little server hand added to the icon them to indicate they are shared?

just saw your edit about samba not working anymore...went to System-Administration, Samba isn't even there, though I'm sharing
files, there is a tab for shared folders, clicking on it gives me a message indicating I don't have the software installed, but I'm
sharing files...strange chit

---

### Post by BMU1 on 2010-09-18
> **macem29 said:**
> in the vista machine when prompted I enterd the only ubuntu pass I have, the one I used when installing
the OS...

I've successfully shared the homefolder, usb drives and SD media...the method I ended up using to get Samba installed did not require the entering of any passwords...do the folders your trying to share have
the little server hand added to the icon them to indicate they are shared?
hmm I tried the password that i have when i installed ubuntu. no luck..

The folder does not have a  server hand icon. it has 2 bi-directional arrows (it is a torrent download folder hence the arrows?). However if i go to 'Places > network' i get a folder called windows network and within that is the folder that is folder called 'workgroup' which is the windows workgroup name. In that i see a server icon named Ubuntu and in that is a folder that i wish to share. If i try to open that folder it says password required, shows my user name, domain = workgroup. But none of the passwords work as the popup gets redisplayed.

---

### Post by BMU1 on 2010-09-18
> **macem29 said:**
> 
just saw your edit about samba not working anymore...went to System-Administration, Samba isn't even there, though I'm sharing
files, there is a tab for shared folders, clicking on it gives me a message indicating I don't have the software installed, but I'm
sharing files...strange chit
:P this just keeps getting better and better!!

---

### Post by macem29 on 2010-09-18
> **BMU1 said:**
> :P this just keeps getting better and better!!

lotsa fun on a Saturday night!

wonder if trying a different folder to share may help...and .the shared icon changes as you change themes,
I used to have the little bi-directional arrows but it became a hand when I switched themes I just recalled 

try setting the share permission with properties tab on another folder and see what happens...it has to be
one you own with the login you are using like desktop or downloads

---

### Post by BMU1 on 2010-09-18
> **macem29 said:**
> lotsa fun on a Saturday night!

wonder if trying a different folder to share may help...and .the shared icon changes as you change themes,
I used to have the little bi-directional arrows but it became a hand when I switched themes I just recalled 

try setting the share permission with properties tab on another folder and see what happens...it has to be
one you own with the login you are using like desktop or downloads
Yup.. at least it makes my Saturday night interesting .. 

I just went back and looked over the post from sandyd. and i double checked her suggestion and realized that while i did change security=shared, that line by default is commented out so i uncommented it and restarted my computer and now the xp computer can see the ubuntu computer but says i dont have permission to access the specified folder.

I created a new folder and dropped a file in it. I right clicked and selected sharing options. selected 'allow others to create and delete files in this folder' and clicked modify share. It gave me a popup about nautilus needing to add some info and i accepted it. The folder icon changed to get the bi-directional arrows.

On XP i set up a new network place. Strangely it didnt ask me for a user/pswd this time and recognized the ip and saved the network connection. But when i try to access it, i get the 'you do not have permissions to access this resorce...'


---edit---
ok.. so i went back to the folder properties and checked the guest access box to allow access with a user account and it worked!!

I'd prefer a login access but this will do for now.

Thanks for all your help, [macem29]("http://ubuntuforums.org/member.php?u=1138418"). Have a great weekend!

---

### Post by sandyd on 2010-09-18
> **BMU1 said:**
> Yup.. at least it makes my Saturday night interesting .. 

I just went back and looked over the post from sandyd. and i double checked her suggestion and realized that while i did change security=shared, t**hat line by default is commented out so i uncommented it and restarted my computer** and now the xp computer can see the ubuntu computer but says i dont have permission to access the specified folder.

I created a new folder and dropped a file in it. I right clicked and selected sharing options. selected 'allow others to create and delete files in this folder' and clicked modify share. It gave me a popup about nautilus needing to add some info and i accepted it. The folder icon changed to get the bi-directional arrows.

On XP i set up a new network place. Strangely it didnt ask me for a user/pswd this time and recognized the ip and saved the network connection. But when i try to access it, i get the 'you do not have permissions to access this resorce...'


---edit---
ok.. so i went back to the folder properties and checked the guest access box to allow access with a user account and it worked!!

I'd prefer a login access but this will do for now.

Thanks for all your help, [macem29]("http://ubuntuforums.org/member.php?u=1138418"). Have a great weekend!
egad!!!!
this is why its hard to help others when your using another Linux Distribution.
Mine comes uncommented by default ;)](*,)

---

### Post by macem29 on 2010-09-18
> **BMU1 said:**
> 
---edit---
ok.. so i went back to the folder properties and checked the guest access box to allow access with a user account and it worked!!

I'd prefer a login access but this will do for now.

Thanks for all your help, [macem29]("http://ubuntuforums.org/member.php?u=1138418"). Have a great weekend!

woo-hoo....congrats my friend, and you have a good one too

---

