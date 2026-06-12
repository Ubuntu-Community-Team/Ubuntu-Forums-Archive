---
title: "Downloading w/out direct internet access"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by hashi856 on 2009-04-15
As far as I know, there is no equivalent to executable files in Linux. This presents a problem for me. I'm in the Army, and I'm in Afghanistan right now. I have no way to connect my laptop to the internet, and therefor cannot download anything. If I were running Windows, I could take a flash drive to a public computer, download the .exe setup file, and transfer it from the flash drive to my laptop. Or I could just run the setup file from the flash drive. Anyway, as far as I know there is no way to do this in Linux. The public computers here run Windows.

Does anyone have any suggestions or possible solutions to my problem?

---

### Post by achase79 on 2009-04-15
you can download .debs and install them separately, but sometimes there are programs that have many dependancies so you would have to download them all which may be too much to do.

---

### Post by bodhi.zazen on 2009-04-15
Try aptoncd :

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by achase79 on 2009-04-15
I script could be written to download all the package lists from ubuntu (which you could use from public computer), another script to update synaptic's lists from the ones downloaded, open synaptic select the programs you want, create a download script, go back and download the .debs and then install them.

It wouldn't be real easy, but is doable if you are persistant.

---

### Post by card_ace on 2009-04-15
my situation isn't quite like yours.  i have dial up internet so i download things at school that has high speed.  use Keryx. just create a system image and then you can choose to download updates from a windows computer

[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

edit: i forgot to mention that keryx will also download all dependencies for you, along with whatever your trying to get.

---

### Post by t0p on 2009-04-15
> **achase79 said:**
> I script could be written to download all the package lists from ubuntu (which you could use from public computer), another script to update synaptic's lists from the ones downloaded, open synaptic select the programs you want, create a download script, go back and download the .debs and then install them.

It wouldn't be real easy, but is doable if you are persistant.

Wow.  That *is* being persistent.

Do you fancy showing me these scripts?  Seems a bit... *persistent*, compared to aptoncd...

---

### Post by Armor Nick on 2009-04-15
If you have another pc with ubuntu on it that does have internet (perhaps put Wubi on it), you could install AptOnCD and create an install cd with your favourite apps. Note: CD-burner is not required since it can load iso files.

EDIT: wow, four posts when I was writing mine...

---

### Post by BDNiner on 2009-04-15
Synaptic has the ability to create download scripts. It is an option in one fo the menus just select the pacakges you want to download and you can create a download script. Take it over to another computer that does have ubuntu and internet access and down the packges there. Take the packages on a thumb drive to you other computer and install them. 

You can also search for DEB files of the software or try to complie the programs yourself from the source code.

---

### Post by llamabr on 2009-04-15
the entire ubuntu distibution is available on a series of cds or dvd.  armed with those, one could use apt to install and remove anything, even when not online.

what sorts of things do you want to get, not online, for example?

---

### Post by llamabr on 2009-04-15
> **hashi856 said:**
> Anyway, as far as I know there is no way to do this in Linux.

One of the best ways to mobilize a group of hackers toward some cause is to suggest that it can't be done in linux.

A guy in my group spent the better part of xmas break installing linux on an ATM, b/c someone suggested he couldn't.

---

### Post by card_ace on 2009-04-15
> **llamabr said:**
> One of the best ways to mobilize a group of hackers toward some cause is to suggest that it can't be done in linux.

A guy in my group spent the better part of xmas break installing linux on an ATM, b/c someone suggested he couldn't.

ain't that the truth!  when i hear someone say it can't be done i prove em wrong.  and i'll add that this site has contributed a lot to my success :lolflag:

---

### Post by hashi856 on 2009-05-01
> **bodhi.zazen said:**
> Try aptoncd :

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)


That would be perfect, but the public computers here run Windows, so there's no way to get the .deb files

---

### Post by fatality_uk on 2009-05-01
You could use [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Each page provides links to the debs and the depependancies required for each package. Any PC, even Windows ;) will let you download everything you need to install an application. You need paitience, but you can get round a lack of netcon by this method.

All the best mate!

---

### Post by lkraemer on 2009-05-01
Sir:
Check out this program.

[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

Thank You, for Serving your Country.  WE SALUTE YOU!
  
lkraemer
USAF

---

### Post by waspbr on 2009-05-01
aside from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")


some other popular software can be found at [http://www.getdeb.net]("http://www.getdeb.net")

---

### Post by mac9416 on 2009-05-02
Keryx will be just right for you. It is a lot like Synaptic except it is portable and cross-platform. You just unzip Keryx onto a flash drive and carry it to the public Windows computer. Then you can download any software in the repositories, Keryx will take care of the dependencies.
Keryx's website is now keryxproject.org, but unfortunately a hosting problem has put it out of order, and the project leader, Excid3, won't be able to take care of it for a few days. If you want, I can post the .zip and the tutorial here.

hashi856, I too salute you for your service.

---

### Post by televisi on 2009-05-02
Hi everyone,
is [http://keryxproject.org/](http://keryxproject.org/) no longer working? as I cannot see anything there?

---

### Post by mac9416 on 2009-05-02
Sorry about the inconvenience, televisi. Keryx's hosting provider had a crash on Friday and the server went down. It should be up in a few days. Until then, I have posted above the latest release of Keryx and a link to its HowTo.

[Tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/")

[Keryx-0.92.zip]("http://launchpad.net/keryx/trunk/0.92/+download/keryx-0.92.zip")

---

### Post by televisi on 2009-05-03
Thanks mac9416!
Will check it out in the next day or so :)

---

### Post by hashi856 on 2009-05-03
Wow, this is more help than I thought I'd get. Thanks a lot everyone, especially mac9416.

---

