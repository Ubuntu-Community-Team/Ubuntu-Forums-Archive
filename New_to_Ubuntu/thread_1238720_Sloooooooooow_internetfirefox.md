---
title: "Sloooooooooow internet/firefox"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by fidelandche on 2009-08-12
Hi,

  My partners laptop is appearing very slow, when you click on firefox the browser opens quickly, but when you type in an address it will respond in about 0.36 seconds, but the problem is this when you click on the link it takes ages to display the web page. It can be pages like Ebay, this forum etc, if you click on a link to say post a thread(like on this forum) it will take a long time to display, so you end up either re-clicking on the link or refreshing the page. I have cleared all private data on firefox, but this has not improved the performance much. I am so used to windows that I am unsure of what to do now. In windows you could also do a check disk, clean up disk and a defrag and all these would improve performance. Can you do any thing of the same in Ubuntu? If not what else is there I can do to improve the performance of firefox?

  Many thanks

---

### Post by WinterMadness on 2009-08-12
In my experience, firefox on linux is actually quite bad with this. it does the same thing to me on any computer i use.

try getting opera or epiphany
opera:[www.opera.com](www.opera.com)
epiphany: sudo apt-get install epiphany-browser

---

### Post by MyR on 2009-08-12
I also use & love opera. The new opera 10 beta is excellent.

You could also try installing the latest firefox (3.5)

checkdisk: linux does a fsck (file system check) every ~30 boots automatically ;]
defrag: linux file systems do not fragment ;]

peace

---

### Post by fooman on 2009-08-12
try creating a new mozilla profile without any added plugins/themes....see if it works any better.

first close any instances of firefox that are open.

next, open your home folder (places > home folder).  when it opens,  click on view in the toolbar and put a check next to "show hidden files",  then scroll down in the home folder and find the .mozilla folder...

right click on it and choose "rename"....rename it .mozilla.bkup

close nautilus and then try firefox again (this will create a new .mozilla folder with a new profile)...see if its any better.

you can get your old firefox settings back by deleting the new .mozilla folder and renaming .mozilla.bkup to .mozilla

hope that helps.

---

### Post by wojox on 2009-08-12
When in doubt tweak it out:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by lovinglinux on 2009-08-12
> **fooman said:**
> try creating a new mozilla profile without any added plugins/themes....see if it works any better.

first close any instances of firefox that are open.

next, open your home folder (places > home folder).  when it opens,  click on view in the toolbar and put a check next to "show hidden files",  then scroll down in the home folder and find the .mozilla folder...

right click on it and choose "rename"....rename it .mozilla.bkup

close nautilus and then try firefox again (this will create a new .mozilla folder with a new profile)...see if its any better.

you can get your old firefox settings back by deleting the new .mozilla folder and renaming .mozilla.bkup to .mozilla

hope that helps.


You can easily  create/delete/start profiles by running the command below:

```
firefox -P
```

Several posts on these forums recommends moving, renaming or deleting **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder to solve Firefox issues. While this will certainly remove any corrupted Firefox profiles and thus solve many common issues, you should consider that the **[COLOR="Sienna"]~/.mozilla[/COLOR]** folder is also the place where other Mozilla applications might store their profiles (Sunbird, etc), so removing this folder will also remove their settings. 

Firefox profiles are stored under **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** folders, where **[COLOR="Sienna"]x.y[/COLOR]** is the Firefox version. So if you need to remove a Firefox profile to fix a problem, then remove **[COLOR="Sienna"]~/.mozilla/firefox[/COLOR]** or **[COLOR="Sienna"]~/.mozilla/firefox-x.y[/COLOR]** not **[COLOR="Sienna"]~/.mozilla[/COLOR]**. 

Nevertheless, there also no reason to delete the entire profile if you can pinpoint the culprit inside it. Most common Firefox issues can be traced back to a single profile file. So, if you can avoid removing the entire profile, you wil be able to preserve other settings like extensions, themes, bookmarks, cookies and passwords.


> **wojox said:**
> When in doubt tweak it out:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

I also recommend that tutorial :)

---

### Post by HermanAB on 2009-08-12
Slowness is usually due to a lame default DNS.  Look at /etc/resolv.conf and test the performance of the DNS using dig (dns tools package). Then put the fastest DNS at the top of the list.

---

### Post by lovinglinux on 2009-08-12
> **HermanAB said:**
> Slowness is usually due to a lame default DNS.  Look at /etc/resolv.conf and test the performance of the DNS using dig (dns tools package). Then put the fastest DNS at the top of the list.

It can also be due to ipv6. See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by gardara on 2009-08-13
disabling ipv6 might speed things up a bit

---

### Post by binbash on 2009-08-13
disable ipv6 :
[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by fidelandche on 2009-08-13
I have disabled ipv6 and that did improve things at the start but everything has just slowed down again. On my laptop I do not have this problem and mine has a lot lower spec than hers. I did try to install the latest version of firefox but was unsure of how to install it, could someone please give me a step by step guide on how to download/install please, as I am very new to Ubuntu and still finding my way about. So far the information on this forum has been very helpful and easy to understand and for someone who has never used code before it is very easy to follow.
 
    Many thanks.

---

### Post by lovinglinux on 2009-08-13
> **fidelandche said:**
> I have disabled ipv6 and that did improve things at the start but everything has just slowed down again. On my laptop I do not have this problem and mine has a lot lower spec than hers. I did try to install the latest version of firefox but was unsure of how to install it, could someone please give me a step by step guide on how to download/install please, as I am very new to Ubuntu and still finding my way about. So far the information on this forum has been very helpful and easy to understand and for someone who has never used code before it is very easy to follow.
 
    Many thanks.

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by fidelandche on 2009-08-15
[LIST=1]
[*]OK I have installed Opera and found it very slow compared with FF, so have removed it. I have also installed Shiretoko, but it appears slower than the version of FF that comes with 9.04. I have tried uninstalling it via add/remove and synaptic and terminal using the following code " sudo apt-get remove shiretoko" but the terminal was unable to find the package, so what do I do to remove it?
[*]Are there any other browsers that work well in Ubuntu?
[/LIST]
                       Many thanks.

---

### Post by lovinglinux on 2009-08-15
> **fidelandche said:**
> [LIST=1]
[*]OK I have installed Opera and found it very slow compared with FF, so have removed it. I have also installed Shiretoko, but it appears slower than the version of FF that comes with 9.04. I have tried uninstalling it via add/remove and synaptic and terminal using the following code " sudo apt-get remove shiretoko" but the terminal was unable to find the package, so what do I do to remove it?
[*]Are there any other browsers that work well in Ubuntu?
[/LIST]
                       Many thanks.


```
sudo apt-get remove firefox-3.5
```

---

### Post by Garyhans on 2009-08-15
Simply go to tools in firefox / addons / extensions and disable ubuntu modifications.  Done. Note they are not enabled in 3.5 which makes the noticeable speed increase.

---

### Post by terry_gardener on 2009-08-15
this has also happened to me before while back now. 
you can also try clearing the cache and browser history. 
open browser and click tools clear option cant remember exact name. 
then close browser and restart it.

---

### Post by sydbat on 2009-08-15
Stupid question time...

Is the Ubuntu install on your partners laptop in a separate partition or via wubi? Wubi can cause problems because it is a virtualization of Ubuntu inside Windows.

Also, is your install (on your own computer) full or wubi? I ask this because you say you have no problems.

Finally, what are the specs on your partners laptop? It might be a hardware issue.

---

### Post by fidelandche on 2009-08-15
The install on my laptop is a full install of jaunty, with vista completely removed. I have also done a complete install of my partners laptop and removed vista, so both have jaunty as the only OS. The specs of my partners laptop are;

Processor 					  					 						 							type : [Intel® Celeron® Processor]("http://www.intel.com/products/processor/celerondualcore/index.htm") T1600   							
						 							clock speed : 1.66 GHz 							
						 							Front Side Bus : 667 MHz 							
						 							2nd level cache : 1 MB 							
						 					 					 				 			 		 			 				 				 					 						 						Operating system 					  					 						 							[Genuine]("http://eu.computers.toshiba-europe.com/images/eu/msg/") Windows Vista® Home Premium 32-bit Edition (pre-installed, Toshiba-HDD recovery)
   							
						 					 					 				 			 		 			 				 				 					 						 						System memory 					  					 						 							standard : 1,024 MB 							
						 							maximum expandability : 4,096 MB 							
						 							technology : DDR2 RAM (800 MHz)   							
						 					 					 				 			 		 			 				 				 					 						 						Hard disk 					  					 						 							capacity : 160 GB 							
						 							certification : S.M.A.R.T.   							
						 							drive rotation : 5,400 rpm 							
						 					 					 				 			 		 			 				 				 					 						 						DVD Super Multi drive (Double Layer) 					  					 						 							compatibility : CD-ROM, CD-R, CD-RW, DVD-ROM, DVD-R, DVD-R(DL), DVD-RW, DVD+R, DVD+R(DL), DVD+RW, DVD-RAM   							
maximum speed : Read: 24x CD-ROM, 8x DVD-ROM/ Write: 24x CD-R, 4x CD-RW, 10x HS CD-RW, 24x US CD-RW, 8x DVD-R, 6x DVD-R (Double Layer), 6x DVD-RW, 8x DVD+R, 6x DVD+R (Double Layer), 8x DVD+RW, 5x DVD-RAM 
						 							type : DVD Super Multi (Double Layer) drive   							
						 					 					 				 			 		 			 				 				 					 						 						Display 					  					 						 							size : 15.4 " 							
						 							type : Toshiba TruBrite® WXGA TFT High Brightness display   							
						 							internal resolution : 1,280 x 800   							
						 					 					 				 			 		 			 				 				 					 						 						Graphics adaptor 					  					 						 							manufacturer : Intel®   							
						 							type : Mobile Intel® GMA 4500M   							
						 							memory : up to 1,340 MB total available graphics memory with 3 GB system memory   							
						 							memory type : shared   							
						 					 					 				 			 		 			 				 				 					 						 						Internal video modes 					  					 						 							The following internal video modes are supported: 							
						 							resolution : 1,280 x 800   							
						 					 					 				 			 		 			 				 				 					 						 						Max External Video Modes 					  					 						 							Max Resolution : 2,048 x 1,536   							
						 							Max Refresh Rate : 85 Hz 							
						 							Non-interlaced resolution with max refresh rate : 1,600 x 1,200   							
						 					 					 				 			 		 			 				 				 					 						 						Interfaces 					  					 						 							1 x DC-in 							
						 							1 x external monitor 							
						 							1 x RJ-11 							
						 							1 x RJ-45 							
						 							1 x external microphone 							
						 							1 x headphone (stereo) 							
						 							3 (Left 2, Right 1) x USB 2.0 							
						 					 					 				 			 		 			 				 				 					 						 						Expansion 					  					 						 							2 x memory slots (1 to configure) 							
						 							1 x ExpressCard slot 							
						 					 					 				 			 		 			 				 				 					 						 						Wireless communication 					  					 						 							Compliancy : Wi-Fi®   							
						 							Network Support : 802.11b/g   							
						 							Wireless Technology : Wireless LAN   							
						 					 					 				 			 		 			 				 				 					 						 						Wired communication 					  					 						 							topology : Fast Ethernet LAN   							
						 							speed : 10BASE-T/100BASE-TX   							
						 							topology : international V.90 modem (V.92 ready)   							
						 							speed : 56 Kbps data and 14.4 Kbps fax   							
						 					 					 				 			 		 			 				 				 					 						 						Sound system 					  					 						 							supported audio format : 24-bit stereo   							
						 							speakers : built-in stereo speaker   							
						 							manufacturer : Toshiba Bass Enhanced Sound System   							
						 					 					 				 			 		 			 				 				 					 						 						Keyboard 					  					 						 							keys : 87   							
						 							Windows keys : Yes   							
						 					 					 				 			 		 			 				 				 					 						 						Pointing device 					  					 						 							type : Touch Pad   							
						 					 					 				 			 		 			 				 				 					 						 						Battery 					  					 						 							technology : lithium-ion   							
						 							maximum life : up to 2h30min (Mobile Mark™ 2007)   							
						 					 					 				 			 		 			 				 				 					 						 						AC adaptor 					  					 						 							input voltage : autosensing AC adapter (100/240 V) for worldwide usage   							
						 					 					 				 			 		 			 				 				 					 						 						Physical dimensions 					  					 						 							W x D x H : 362 x 267 x 33.0 (front) / 37.7 (rear) mm 							
						 							weight : starting at 2.49 kg 							
						 					 					 				 			 		 			 				 				 					 						 						Warranty 					  					 1-year international warranty. Upgrade your standard warranty with Toshiba warranty extension, uplift and all-risks insurance packs. 
						 					 					 				 			 		 			 				 				 					 						 						Bundled hardware 					  					 						 							AC adaptor  							
						 					 					 				 			 		 			 				 				 					 						 						Bundled software 					  					 						 							Toshiba Disc Creator  							
						 							Toshiba User's Manual  							
						 							Supervisor Password Utility  							
						 							Toshiba Assist  							
						 							Toshiba DVD Player  							
						 							Ulead® DVD MovieFactory® for TOSHIBA  							
						 							McAfee® Internet Security Suite - Toshiba Edition (includes free Internet updates for 30 days)  							
						 							Toshiba Recovery Disc Creator  							
						 							Microsoft® Works, Microsoft® Office Home and Student 2007 (free 60-day trial)  							
Toshiba Value Added Package (Toshiba Power Saver, Toshiba Zooming Utility, Toshiba PC Diagnostic Tool, Toshiba Flash Cards, Toshiba Components Common Driver, Toshiba Accessibility, Toshiba Button Support) 
						 							Google Software (Google Toolbar for Internet Explorer, Google Desktop, Picasa)  							
						 							Connectivity Doctor  							
						 							ConfigFree™  							
						 							Toshiba utilities and drivers  							
						 					 					 				 			 		 			 				 				 					 						 						Toshiba EasyMedia 					  					 						 							Google Software (Google Toolbar for Internet Explorer, Google Desktop, Picasa)  							
						 							Toshiba TEMPRO Performance Tuning Service  							
						 							McAfee® Internet Security Suite - Toshiba Edition  							
						 							Smart Display Support  							
						 							Toshiba Flash Cards  							
						 							Diversity Antenna  							
						 							Toshiba ConfigFree™  							
						 							Internal HD 720p support  							
						 					 					 				 			 		 			 				 				 					 						 						Security features 					  					 						 							user password  							
						 							main memory (by screw)  							
						 							HDD password on request  							
						 							main battery pack (by sliding latch)  							
						 							wireless LAN switch  							
						 							main hard disk (by screw)  							
						 							slot for Kensington Cable Lock  							
						 							supervisor password  							
						 					 					 				 			 		 			 				 				 					 						 						Special features 					  					 						 							HD Audio support  							
						 							SM BIOS compliant  							
						 					 					 				 			 		 			 				 				 					 						 						Certification 					  					 						 							This product is in compliance with the requirements of the applicable European Directives for CE marking. 							
						 					 					 				 			 		                                             	                                                                                                                                                                                                                                                                                                                                                                                                                                             [                                                                                              ]("javascript:window.open('/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=UK&com.broadvision.session.new=Yes&PRODUCT_ID=1058194&printFriendly=true','printFam','menubar=yes,toolbar=no,status=no,width=850,height=450,scrollbars=yes,resizable=yes');void(null);")                                                                                                                            
                                     	                                                                                                                                                                                                                                                                                                  [SIZE=3]I have cleared the cache and browser history 
[/SIZE]

---

