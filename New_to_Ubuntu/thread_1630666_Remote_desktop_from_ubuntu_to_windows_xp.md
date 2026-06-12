---
title: "Remote desktop from ubuntu to windows xp"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by inhifistereo on 2010-11-25
I am both an absolute beginner and lazy so please bear with me here.

I have an HP laptop loaded with ubuntu 10.04 LTS and an older 32-bit desktop running Windows XP Home edition.  The laziness streak in me would like it if there was a way to remote desktop from the ubuntu laptop to the Windows box from the comfort of my couch.  It would seem that XP Home limits me quite a bit from a remote desktop perspective.  To get around this, Google searches have instructed me to use the built-in Terminal Server Client, tightvnc, realvnc, ultravnc, etc.  I tried the Terminal Server Client but I continually get an error stating something along the lines of (I can post a screenshot if you're interested):  

Autoselect keyboard map en-us
ERROR: channel_register

Any help/insight would be greatly appreciated.  Thanks.

---

### Post by 12apennachi on 2010-11-25
I am assuming you want access to the ubuntu machine from windows, correct?

If so go to prefeerences-> Remote Desktop and make sure it is set up to be accessible. Then install xrdp.

sudo apt-get install xrdp

Go to the windows machine and use the terminal server client and type in the ip given in the remote dektop window. Type in your username and password where necessary and it should work

---

### Post by kroq-gar78 on 2010-11-25
> **12apennachi said:**
> I am assuming you want access to the ubuntu machine from windows, correct?

If so go to prefeerences-> Remote Desktop and make sure it is set up to be accessible. Then install xrdp.

sudo apt-get install xrdp
I think he means windows from ubuntu

---

### Post by marl30 on 2010-11-25
Try Teamviewer:  [http://www.teamviewer.com/index.aspx](http://www.teamviewer.com/index.aspx)

Download the deb from the site and install to Ubuntu. Add the exe to XP then set it to auto start with XP. I use it at home to remotely work between computers.

---

### Post by 12apennachi on 2010-11-25
Oh, my bad, well in that case I can't help much here, not an experienced windows user. Not experienced in Ubuntu either but I did get my ubuntu to be accessed remotely via rdp and vnc.

---

### Post by karthick87 on 2010-11-25
I personally prefer Team  viewer,it's a computer software package for remote control, desktop  sharing, and file transfer between computers. The software operates with   Microsoft Windows,Linux based OS & Mac OS X, and is able to  function while the computers are protected by firewalls and NAT  proxy....
  **Installing Team viewer:**
  For Ubuntu,you can download teamviewer [here]("http://www.teamviewer.com/download/teamviewer_linux.deb"). Once downloading is completed, you can install it easily by double  clicking the file.After installation you can find team viwer under the  Internet Menu.
  **Open the Team Viwer:**
  Applications -- >>Internet -->> Team Viwer
  [IMG]http://i.imgur.com/eWwZs.png[/IMG]
  Before establishing the remote desktop connection,you must know the  ID and Password of the remote system which is running Team Viwer.After  getting the ID and Password from your partner.Enter the ID and click  connect to partner, with in few seconds it will show a window prompting   for a password.Enter the password which you got from your partner and  click ok.
  Now you are connected to remote sytem.

---

### Post by inhifistereo on 2010-11-25
You are correct kroq.  I want to connect to windows from ubuntu.

I've been doing a little more research.  I ran across this article on lifehacker:

[http://lifehacker.com/5080121/five-best-remote-desktop-tools](http://lifehacker.com/5080121/five-best-remote-desktop-tools)

With teamviewer, will the ID be static? And is there a specific ID for the laptop and a specific one for the desktop?

The article links to [another how-to]("http://lifehacker.com/software/feature/geek-to-live-how-to-control-your-home-computer-from-anywhere-125607.php") on setting up TightVNC.  

It looks like I've narrowed down my search: TightVNC vs. Teamviewer.  With TightVNC I probably won't have to mess with any firewall issues since I won't be accessing the desktop from outside my home.  But Teamviewer looks like its a little easier to manage.  Thoughts?

---

### Post by karthick87 on 2010-11-25
Yes you can set the static id for team viewer.

---

### Post by gary0 on 2010-11-25
You can't remote desktop to xp home edition, it is a feature not included in that version.

---

### Post by marl30 on 2010-11-26
> **inhifistereo said:**
> You are correct kroq.  I want to connect to windows from ubuntu.

I've been doing a little more research.  I ran across this article on lifehacker:

[http://lifehacker.com/5080121/five-best-remote-desktop-tools](http://lifehacker.com/5080121/five-best-remote-desktop-tools)

With teamviewer, will the ID be static? And is there a specific ID for the laptop and a specific one for the desktop?

The article links to [another how-to]("http://lifehacker.com/software/feature/geek-to-live-how-to-control-your-home-computer-from-anywhere-125607.php") on setting up TightVNC.  

It looks like I've narrowed down my search: TightVNC vs. Teamviewer.  With TightVNC I probably won't have to mess with any firewall issues since I won't be accessing the desktop from outside my home.  But Teamviewer looks like its a little easier to manage.  Thoughts?

Teamviewer is simpler than any such software I've messed around. It got me over my intimidation of connecting remotely to another computer. Once it is installed on each computer, it's just a matter of copying the id that will show up in teamviewer for the computer you want to connect to, then enter it into teamviewer on the other one, and it will connect without requiring any further configuration.

---

