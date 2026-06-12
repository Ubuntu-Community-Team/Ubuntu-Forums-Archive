---
title: "Failure to find network printer driver/general share headaches"
date: 2022-04-16
forum: Networking &amp; Wireless
---

### Post by tsaker2 on 2022-04-16
Not sure how to approach this, so I'll just jump right in.

Printer headaches: After a laptop SSD crash, installed a fresh U 20.04.  Although CUPS found and loaded the correct driver for my home printer,  it will not find/load the correct driver for my office printer. It will  not find the network printer automatically. When searching by either  samba or ipp, I have to input the information manually, and search for a  driver. Although the model is listed, and 4 selections are offered,  none of them are like the name of the driver loaded on my office desktop  running U 18.04 (has the correct driver used in that and previous LTS  versions) and prints properly. Using any one of the selected drivers to  print a test page yields a couple of lines of gibberish. If the  operation isn't halted, the printer will continue to spew blank pages.  In other words, neither CUPS nor the native U printer menus will  properly add a printer.

General share headaches: My office desktop sees other U machines and a  Win 7 box but won't connect with them. I can connect to my office  desktop with my laptop using nautilus's the "connect to server" box by  entering the url and folder name. However, the desktop sees the laptop  but will not connect to it either with the gui or url/folder. On my home  network, my laptop  can see other U machines but no Win machines of any  version appear. I just had to re-add the home printer on the laptop   manually just now - it found the correct driver and printed out a  correct test page. When it added this printer automatically upon  completion of the setup, the thing would not print.

I can't count the number of pages I have looked at to try and solve my  folder sharing headaches. I have edited the smb.conf files on several of  my U boxes (which solved the seeing issues but not access issues), gone  through user groups, allowed samba through the firewall (using  firewall-config and command line for ufw), used nautilus to enable  sharing of the specific folder, and still no joy. Some of the pages  imply that a recent vulnerability has resulted in the deprecation of  SMB1 and the samba configuration gui, leaving the entire thing in the  realm of CLI, manual file editing, and apparently hit-or-miss choices in  other GUI-oriented programs. I have not been able to find anything that  addresses my apparently unique problems, and have a hard time believing  that networking with U (and/or with windoze) has become so difficult.

That being said, am I doing something wrong here? Any advice would be appreciated.

---

