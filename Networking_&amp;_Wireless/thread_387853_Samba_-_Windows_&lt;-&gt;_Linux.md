---
title: "Samba - Windows &lt;-&gt; Linux"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by rianquinn on 2007-03-18
I've been using Ubuntu for 2 years now and I still cannot get samba to work correctly. When I click on System->Shared Folders and add a folder to share everything works between Linux boxes. However, I get a login screen on my windows boxes and when I enter a user name and password, I get nothing. 

So I followed the Ubuntu Guide and added the User name stuff and Windows can now talk to Linux. But Linux cannot talk to Windows. 

How do you setup Windows Networking in Ubuntu via GUI so that I get Windows <-> Linux. 

Thanks,
Rian

---

### Post by scxtt on 2007-03-18
have you tried:

smb:/<ip address of windows box>/<samba share name>
(ex. **smb:/192.168.0.100/windows_share**)

from Nautilus/Konqueror/Thunar?  Are you sure a windows firewall isn't blocking anything?

---

### Post by matneym on 2007-03-18
I've been having the same problem. My desktop PC and laptop see my Linux box with no problem. Linux sees the network but can't see the shared folders on the other PC or laptop. I've turned off all the firewalls but still haven't had any luck.

---

### Post by scxtt on 2007-03-18
the whole "network neighborhood" feature b/t Linux <-> Windows doesn't always work quite well w/o a bit of fiddling ... i've seen it not work @ all, and other times work seamlessly ...

so my recommendation, to start off with, is ALWAYS use the IP address of the samba host w/ a smb:/ capable file browser to see if shares you KNOW exist show up ...

---

### Post by rianquinn on 2007-03-19
Is there a way to report this to the Ubuntu Developers. I mean this seems like something that Ubuntu should support out of the box. I mean I would imagine almost all small businesses use Windows Networking.

Rian

---

### Post by scxtt on 2007-03-19
eh, i don't think there's a real "problem" - it works - there are just differences b/t how each DE handles "Network Neighborhood" ... so it's not something for the ubuntu devs, but more for the gnome devs or kde devs ... but again, i'd hardly think of it as an issue ...

---

### Post by dmizer on 2007-03-19
try doing this:

```
sudo aptitude install smbfs
```
or, if you want to avoid the command line completely, just look for the "smbfs" package in synaptic.

then try to connect with places > connect to server and you should get better results.

that said, using nautilus as above to connect to a windows share is at best ... iffy.  it only takes a little bit of effort to configure it via command line, and  your experience will be much more pleasant.  configuring via command line allows you much higher speeds, and the ability to transfer files larger than 2gb.

---

### Post by rianquinn on 2007-03-20
Do you mean configure nuatalis via command line or samba. I guess I would have no problem setting up either if I had a good reference. I know from experience that the Ubuntu Guide doesn't work.

I'm still confused as to why the Ubuntu Developers haven't addressed this problem. What do other people use/do for Windows Networking. I cannot be the only one.

Rian

---

### Post by dmizer on 2007-03-20
as indicated previously, it's not really an ubuntu issue.  it's more of a failure for nautilus to integrate well with samba.  also try to remember that samba file sharing is a NON native linux app.  samba is a windows networking invention, so it has quirks and nuances that a native linux file sharing application (like nfs) does not.

as far as how people handle the problem, i'm sure many people flat give up.  in any case, the way i deal with the issue is by trying to offer as much support in the area as i can.  in this particular case, i wrote a howto that can be found in the second link in my sig.

---

### Post by rianquinn on 2007-03-20
you have a very impressive How To. In Fact there is a folder that I will try to mount. Do you know of a GUI that can browse a Windows Network. I ask this because I have several folders that are accessed on a not so regular basis and it would be foolish to mount them.

---

### Post by dmizer on 2007-03-20
you can still add them to the fstab line with the "noauto" option.  then they won't automatically mount when you boot.  like so:
```
//netbiosname/sharename    /media/sharename        cifs    [COLOR="Red"]noauto[/COLOR],guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
now ... when you want to mount your periodic share, just issue the following command in your terminal:
```
sudo mount /media/sharename
```
(where "sharename" is a unique name to each share) it'll take you far less time than trying to browse through some gui.

---

### Post by scxtt on 2007-03-20
and i can pretty much guarantee you that opening nautilus and doing:

smb:/<ip address of windows box>/

in a location bar will allow you to see all samba shares a host has to offer ...

hell, i can even open up an old version of RH and type "smb:/" into a location bar and get all the samba hosts ...

---

### Post by rianquinn on 2007-03-21
I'm sure you can enter an IP address but my computers use DHCP. I'm still surprised it has to be this difficult. If nautalis is in fact the problem, how can we fix it. Is there at least another way to network a windows machine to a Linux machine easily? What do people use?

---

### Post by dmizer on 2007-03-21
some people indicate that they have acceptable success by switching to kde (kubuntu).  konqueror is apparently able to handle the issue better.  many people don't experience a problem at all.

if you can code, contact the developers of nautilus here: [http://www.gnome.org/projects/nautilus/developers.html](http://www.gnome.org/projects/nautilus/developers.html) ... this is a project completely independent of ubuntu so as a forum, there's not a lot "we" can do other than offer alternatives.  but nautilus is only PART of the problem.

another part of the problem is simply having a correctly configured network which has everything to do with the windows side of things.

if your network is dhcp, you just need to make sure all your windows boxes have netbios installed and enabled (most xp machines have this turned on by default).  then visit: start > control panel > system > computer name tab.  select "change" and give each box a unique name that you will be able to remember.

also, make sure they are all a part of the same workgroup. sometimes they are mshome, sometimes they are set to workgroup, but you can set it to whatever you want as long as EVERY computer belongs to the same workgroup. but in order for everyone to see each other, the workgroup should be the same.

now, when you browse to your computers on your network, you can browse by their name instead of by their ip address.  so for example from scxtt's suggestion, browse to the following address:
```
smb://computername/
```
this should work (when using "computername", it DOES require two slash marks "//" instead of only one shown in scxtt's posts) every time no matter what ip the machine picks up.  furthermore, if you make sure that ALL your computers on the network belong to the same workgroup, you may find that your nautilus issues have resolved themselves.

if it still doesn't work, you'll need to make sure that windows xp (or third party) firewall isn't blocking connections (this often changes without warning when you update windows).

or ... you can just set it all up with fstab and use:
```
sudo mount /media/sharename
```

---

### Post by scxtt on 2007-03-21
> (contrary to scxtt's posts, it DOES require two slash marks "//" instead of only one shown)i can provide screenshots, for both gnome and kde - that show that smb:/ works ... and if i do "smb://" in konqueror, i get an "http://smb//" error ...

maybe ubuntu is different, but here at work where we have a HUGE samba setup, smb:/ works (as far as browsing all workgroups) w/ the Red Hat we use ...

but it does look like:

smb:/WORKGROUP_NAME ends up resolving itself to smb://WORKGROUP_NAME in KDE ... i will admit that in Gnome, smb:/WORKGROUP_NAME doesn't work :( ...

---

### Post by al7kz on 2007-03-21
x

---

### Post by dmizer on 2007-03-21
> **scxtt said:**
> i will admit that in Gnome, smb:/WORKGROUP_NAME doesn't work :( ...

this was my point.  i've edited my post to make that more clear.  sorry about that.  also, if the share names have non-ASCII characters in their names (in my case japanese), the single slash will also cause problems.  further ... i don't have any problem opening smb://ipaddres or smb://workgroup_name in either kde or gnome.

---

### Post by scxtt on 2007-03-21
well, we all have different experiences - for me smb:/ has always worked, so (i'm just so used to smb:/ that typing it is a reflex) ... we were both right, but you're a bit "righter" :) ...

---

### Post by dmizer on 2007-03-21
> **scxtt said:**
> but you're a bit "righter" :) ...

lol!  thanks for that, that just made my day.  excuse me while i polish my "a bit righter" badge :popcorn:

---

