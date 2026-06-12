---
title: "realtek c811 usb wifi driver install"
date: 2018-11-19
forum: Networking &amp; Wireless
---

### Post by spunabearing on 2018-11-19
ac 600 c811 realtek  usb wifi instrucktions

       open terminal type     lsusb       should see in list

go to -   [https://github.com/ulli-kroll/rtl8821cu](https://github.com/ulli-kroll/rtl8821cu)     -download zip.

extract it and move that file to your Home Folders  rtl8821cu-master

open terminal    sudo apt purge rtl8821cu-dkms
                            cd rtl8821cu-master
                            make clean
                            make
 Somewhere along the way as its compiling it says it needs a dev flie to be installed!!!

                           sudo apt-get install   (WATCH FOR FILE NAME AS ITS COMPILING
                                    IS A DEV FILE COPY IT IN)    hit enter.

   Then               sudo make install

                          sudo service NetworkManager restart
                         
        NOW RESTART

Sorry I'm new at this hope it helps.Took me a week of trial and error!Don't give up.

---

