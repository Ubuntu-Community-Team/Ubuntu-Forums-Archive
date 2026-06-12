---
title: "display not being found!!!"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by penn2014 on 2010-03-18
hi guys.... u have a gateway monitor made in 2002. i am trying to hook it up as a second monitor. the power light is on but nothing shows up. 



i would be extremely grateful for anyones help..

thanks

---

### Post by GSF1200S on 2010-03-18
> **penn2014 said:**
> hi guys.... u have a gateway monitor made in 2002. i am trying to hook it up as a second monitor. the power light is on but nothing shows up. 



i would be extremely grateful for anyones help..

thanks

What kind of video card do you have? Are you connecting both monitors to one video card, or do you have 2 video cards with one monitor connected to each? Can you post the results of:
```
lspci
```

Once we get this information, we can try to help you out :)

---

### Post by penn2014 on 2010-03-18
here they are



00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)                                                                   
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)                                                                    
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)                                                           
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)                                                           
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)                                                           
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)                                                           
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)                                                              
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)                                                              
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)                                                              
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)                                                              
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)                                                     
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)                 
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)                                                                     
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)                                                            
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)                                                                       
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)                                                                  
01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)                                                                          
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)                                               
06:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)           
06:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)    
06:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem 
06:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)                  
lenny@lenny-desktop:~$ 000:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)                                                                                                                           
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)                                                                                                                             
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)                                    
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)                                    
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)                                    
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)                                    
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)                                       
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)                                       
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)                                       
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)                                       
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)                              
bash: syntax error near unexpected token `('                                    
lenny@lenny-desktop:~$ 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 01:00.0 VGA compatible controller: nVidia Corporation NV45 [GeForce 6800 GTO] (rev a2)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 17)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 06:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 06:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
bash: syntax error near unexpected token `('
lenny@lenny-desktop:~$ 06:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
06:02.0: command not found
lenny@lenny-desktop:~$ 06:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)



thanks

---

### Post by GSF1200S on 2010-03-18
Have you enabled the Nvidia driver for your first screen? First open a terminal and do:
```
sudo apt-get update
```

Then, go to System > Administration > Hardware Drivers. It should tell you that you are currently running the Nvidia drivers. If not, enable and install the drivers by clicking 'Activate.' You will have to reboot after they are installed.

Finally, open a terminal and type:
```
sudo nvidia-settings
```

In the window that follows, go to X Server Display Configuration (in the left pane). You should see your other monitor listed as 'Disabled.' Enable the second monitor. Then, you will need to select whether you want to use Xinerama, Twinview, or a Seperate X-screen. Once selected, hit Apply and the click Save to X Configuration File. Done. Restart X with the following command and the second screen should work:
```
sudo /etc/init.d/gdm restart
```

---

### Post by penn2014 on 2010-03-18
ok thank you very much i will try that and get back with results

---

