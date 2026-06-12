---
title: "intel acl 1200 or previous version etc, ati hdmi, how to get sound in 9.10 or 10.04"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Trinity33 on 2010-02-27
i wanted to try help those ones who strugle with sound card in kamic or lucid. so lets begin :) im new to ubuntu really and so i had a lot of bad experience with my sound card graphic etc. my laptop spec msi gt 725 cpu q9000 graphic ati hd4850 sound intel acl 1200 buid in and hd48x0 ati hdmi build in 5 speakers. First i tested interpid and maybe cos its older distro i didnt have any problems with my graphic or sound card etc the problems started in karmic and lucid alpha2. i will explain how did i make my sound card work in karmic and the same system work in lucid. first i installed my new karmic and there from the beggining started truble cpu went to 40 or 50% ram too i downloaded ati catalyst new one from ati web site and that fixed graphic problem. there is no support for ati in lucid yet. so if u have ati card better not to use lucid at the moment i think. about my sound card when i booted karmic there was useless broken sound from just one speaker. so i started read about alsa oss oss4 pulseaudio etc etc. and really tried everything to make my card any of my sound cards working and i couldnt jutst today i found solution. there is no need to remove pulse audio or anything so im talking about fresh karmic install. 
first boot your new karmic and check if your card is recognised or not by:
aplay -l
output from my card:
List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
so i got acl1200 and ati hdmi. i want to say that there is no support from alsa or oss oss4 for ati hdmi and i dont think for nvidia too. everything u can get is sound from your card 0 device one acl1200digital 5.1 surround if u got more then one speaker
second step:
i assume that u have updated your repistories  using synaptic if not then need update (and dont remove any drivers any pulse or any libraries etc)after that type in the shell:
cat /proc/asound/version
i got advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb 27 2010 for kernel 2.6.31-14-generic (SMP) my driver is the newest one from alsa.org let assume u just installed karmic and want to update your alsa driver. so first stop your utils by:

sudo /etc/init.d/alsa-utils stop  

then get few new tools by typing:

sudo apt-get -y install build-essential ncurses-dev gettext xmlto  libasound2-dev
sudo apt-get install patch 
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

the next step is to get some alsa drivers oss wouldnt work with new cards to be honest i tried it for long time and it doesnt. 

so the next step go to:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

u will find over there linux package download it. there u will get alsa driver utils tools lib and codecs.

so u downloaded unpack it whatever u want to then:
cd first package:
 my is  cd '/home/trinity/Desktop/realtek-linux-audiopack-5.14/alsa-driver-1.0.22'
then :

sudo ./configure --with-debug=full --enable-dynamic-minors --with-moddir=updates

then:
make and sudo make install

u shouldnt have any problems if u running fresh karmic.
after that cd to lib folder:

sudo ./configure then make and sudo make install

after that cd plugins then sudo ./configure make and sudo make install

then cd utils then sudo ./configure and sudo make install skip make

so u got everything installed if u want newer driver u can go to alsa.org and download newest driver or library the ones from realtek are ok too. .
so now u got driver and everything installed restart your pc. then check your driver version u should see the one u just installed:

cat /proc/asound/version

then open shell and type alsamixer check if everything is unmuted if not unmute evrything then if u got two cards press f6 and check the other card unmute MM mean mute OO unmute.
u can double check if your cards are detected by:

aplay -l if so close everything and in new shell u can or no need type:
alsaconf 
there u will be able to select other card if u want to but cos there is no support for hdmi then to be honest no need to open alsaconf.
if u still dont have flash plugin cos u just installed your karmic open synaptic type in search box flash player and install it..
Now test your card if is working open youtube type in search box bob marley open one love song and see if there is sound coming out of your speakers if yes then u are lucky your card is working u can test it using also by palying something from your desktop usind for example vlc media player[FONT=monospace]. i like that one cos movie palyer or alsa didnt work well for me.
Now we assume that your sound still doesnt work if so there is one thing u do and it will work it worked for me:) and will work for any i think other analog digital sound card just not hdmi(didnt test it that way maybe will in the future at the moment im happy from what i got :)). so if u got bad sound or no sound then just look dont do anything yet at this models:
[/FONT]3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  arima        Arima W820Di1
  targa        Targa T8, MSI-1049 T8
  asus-a7j    ASUS A7J
  asus-a7m    ASUS A7M
  macpro    MacPro support
  mb5        Macbook 5,1
  mbp3        Macbook Pro rev3
  imac24    iMac 24'' with jack detection
  w2jc        ASUS W2JC
  3stack-2ch-dig    3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig    6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire    Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion    Medion Laptops
  medion-md2    Medion MD2
  targa-dig    Targa/MSI
  targa-2ch-dig    Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e    Lenovo 101E
  lenovo-nb0763    Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66    Haier W66
  3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell    Dell machines with 6stack (Inspiron 530)
  mitac        Mitac 8252D
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a    Intel IbexPeak with ALC889A
  intel-x58    Intel DX58 with ALC889
  asus-p5q    ASUS P5Q-EM boards
  mb31        MacBook 3,1
  sony-vaio-tt  Sony VAIO TT

now press alt+f2 window will open type gksudo nautilus then go to folder /etc/modprobe.d/ there will be sound file open it
[FONT=monospace]

[/FONT]ok now u see probably few lines something about your card delete it and past this lines dont close or save it yet:

   
options snd-hda-intel model=targa
options snd slots=snd-hda-intel
# u1Nb.hSHNs4ufGJ5:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intelthe model=targa u can change to anyone from the list i showed above i used model=targa-8ch-dig u can try everyone and chose best one for your card. i asume that u know now how to do it. so now save this file and close window then u can use
 command  [FONT=Courier New][SIZE=3][COLOR=Red]**su -c  'rcalsasound restart'**[/COLOR][/SIZE][/FONT] to restart your alsa if it fail then restart your pc in that way i got my sound card working alc1200 digital 8 channels sound from 5 speakers. after restart if your card still have problems go back to modprobe.d sound open it and use different model.
restart pc and try it again. 
i didnt uninstall any pulse audio any oss or any alsa drivers my sound card is working better then under win7 now im happy and everything i did was by myself wanted to share my info to help others. this i workign tutorial for lucid and karmic for every intel card  and didnt test if would work with hdmi will stil do some tests maybe it will work so thanks for reading and good luck.

---

### Post by petrosy on 2010-03-30
Works great with Asus P5Q-EM Ubuntu 9.10 :KS

---

