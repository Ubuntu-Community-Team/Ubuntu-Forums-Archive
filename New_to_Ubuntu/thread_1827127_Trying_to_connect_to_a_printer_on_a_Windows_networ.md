---
title: "Trying to connect to a printer on a Windows network"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by PaddyIndigo on 2011-08-17
Hi,
I'm using a Canon Pixma MP282,  attached to a Windows XP machine and I want to print to it from my Ubuntu machine on the same network.

The Ubuntu machine finds the printer ok, and the verify button confirms that the print share is accessible,  but when when I click on the forward button it asks me to choose a driver,  and the Canon Pixma MP282 is not an option.

I downloaded the driver in a tar file,  opened it with the archive manager, which gave me three files with ugly names ending in tar.gz,  selected them all and clicked extract,  but I still don't get an option to select it.

What am I doing wrong?

Thanks
Pat

---

### Post by HalfEmptyHero on 2011-08-17
Can you give me a link to the driver you downloaded? You most likely have to build the drivers yourself. There should be a file named README or install or something like that with instructions.

---

### Post by pi.boy.travis on 2011-08-17
You'll likely have to compile those drivers yourself. If you can find a PostScript file for the printer, that would be ideal, try Google. Alternatively you could search Synaptic with your printer name and/or model number to see if there are drivers available in the repositories.

---

### Post by PaddyIndigo on 2011-08-18
> **HalfEmptyHero said:**
> Can you give me a link to the driver you downloaded? You most likely have to build the drivers yourself. There should be a file named README or install or something like that with instructions.

The download is at;
[http://software.canon-europe.com/software/0040266.asp?model=](http://software.canon-europe.com/software/0040266.asp?model=)

Thanks

---

### Post by PaddyIndigo on 2011-08-18
> **pi.boy.travis said:**
> .... you could search Synaptic with your printer name and/or model number to see if there are drivers available in the repositories.

I get the following error when I run synaptic;

[COLOR=RoyalBlue][I]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/I][/COLOR]
And synaptic exits.

Could this be because I tried to unpack the tar files myself?

I get the same message whether I run synaptic or "sudo synaptic"

Any ideas how to fix?

---

### Post by PaddyIndigo on 2011-08-18
> **PaddyIndigo said:**
> I get the following error when I run synaptic;

[COLOR=RoyalBlue][I]E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/I][/COLOR]
And synaptic exits.


I found the solution in [this link]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Encountered+a+section+with+no+Package%3A+header&as_qdr=all&sa=Google+Search&lang=en#1050") =

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

which seems to have fixed the error.  I'll get back with an update about whether the original issue is solved

Thanks
Pat

---

### Post by PaddyIndigo on 2011-08-18
Progress! 
I've fixed the error message,  but I am still not able to connect to the printer. I'm still getting as far as the select driver screen,  and no driver is appearing.

I've searched synaptic, but haven't found anything. However I'm not sure whether I'm using synaptic correctly.

---

### Post by corncob on 2011-08-18
Myself and others have given advice on a similar printer:
[http://ubuntuforums.org/showthread.php?t=1826100](http://ubuntuforums.org/showthread.php?t=1826100)
So far we have not gotten a reply from the OP.

---

### Post by PaddyIndigo on 2011-08-18
I tried the suggestions in your link.
The download I have looks the same as the one linked, & I executed the lines given in the link (code pasted here);
     Code:
     sudo add-apt-repository ppa:michael-gruz/canon 
     sudo apt-get update
     sudo apt-get install cnijfilter-mp280series 

But I still can't connect to the printer.  I think there is some basic step that I'm missing. because when I open a cnijXXX .deb file in the software centre that has appeared on my disk at some point along the way it says "A later version is already installed"

I'll go over what I'm doing and maybe you'll see what I'm leaving out;
1. I locate the printing icon in files and folders & launch it.   I have no printers installed.
2. I cl.ick the "Add" button
3. I select "network printer" - "Windows printer via samba"
4. I click the "Browse" button and browse to the printer.
5. I click the verify button and it confirms the print share is accessible
6. I click forward and the "Select printer from database" radio button is already selected by default. I can't take the "Provide PPD file" option because I don't have a PPD file,  and the "Search for a printer driver to download" option doesn't find my printer either.
7. I click Canon in the "Makes" window.and click "forward"
A long list of printers is displayed but no MP280 series

Anything look wrong there?

Thanks,
Pat

---

### Post by corncob on 2011-08-18
Does this printer have a LAN (Ethernet) port so that you can plug it directly into your router (after disconnecting it from the computer)?  That way you will have a "network printer" rather than a "windows printer" and everybody can use it.

---

### Post by PaddyIndigo on 2011-08-19
No, no LAN port.

Based on what I've done,  should I expect to see my printer in the list at #7 in my previous entry?

Thanks, 
Pat

---

### Post by corncob on 2011-08-19
Here's a long thread on the MP280 with several success stories:
[http://ubuntuforums.org/showthread.php?t=1582497](http://ubuntuforums.org/showthread.php?t=1582497)

---

### Post by PaddyIndigo on 2011-08-19
E U R E E K A  !!!

I've printed a test page! 

I tried this before I saw Corncob's last link,  but I'll take a look at that too,  because what I did,  although it worked,  was a bit of a kludge.

What I did,  having gone through everything I described above, was simply to plug the printer directly into the Ubuntu machine and it installed itself automatically as a local machine.  Then I plugged the printer back into my Windows machine,  and changed the local printer properties to the address of the windows machine.

A L L E L L O U E E E Y A H O O !!!!

Thanks to everyone that contributed to this thread.
Pat

ps
Any delay in posting this response is due to the time it took to get out  of gaol,  having been arrested for running naked thro' the streets,   screeching insanely in triumph!!!

pps
I'll update with how I get on with Corncob's link.

---

