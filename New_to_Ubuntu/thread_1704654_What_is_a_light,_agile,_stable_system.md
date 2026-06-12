---
title: "What is a light, agile, stable system?"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by 007casper on 2011-03-10
I want to run linux on an arm cortex A8 base chip set.  What would be the best system?  

Xfce, xubuntu, ubuntu netbook, slackware etc

---

### Post by NightwishFan on 2011-03-10
Try ubuntu with a minimal install with what you want, or Debian. Those are the only systems I really recommend these days.

---

### Post by bwang on 2011-03-11
Debian.
Or Arch, if you have some Linux experience.

---

### Post by Legeril on 2011-03-11
Try Xubuntu? Thats very lightweight and as stable as other Ubuntu's

---

### Post by el_koraco on 2011-03-11
lubuntu, debian, or if you want a lego-like window manager that you can tweak any way you want, bodhi linux.

---

### Post by mcduck on 2011-03-11
...just keep in mind that not very distribution has a variant for ARM processors. And even then you might not have all the same programs available as you'd have on a x86/x86-64 version.

I'd go for a minimal Ubuntu or Debian install, both support ARM and can be very lightweight if you just choose your desktop and programs wisely. (Also note that,a t least with Ubuntu, there are no ARM versions of the XUbuntu, Kubuntu or Lubuntu available. you need to use the normal  or mminimal Ubuntu install and add the desktop you want).

So, from the suggested options, you can rule at least Xubuntu (apart from installing XFCE yourself), Arch and Bodhi Linux out. None of those are available for ARM.

---

### Post by Matt__ on 2011-03-11
specifically designed for ARM is linux [Linaro]("http://www.linaro.org/downloads/")
it has a completely cli option or a netbook style interface.

---

### Post by NightwishFan on 2011-03-11
Linaro and Ubuntu work together I think. Also the ubuntu gcc version is:
```
gcc --version
gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5
```

---

### Post by 007casper on 2011-03-11
[http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)
> 
These showed that Xubuntu used more than twice the RAM as Debian in simple tasks. Xubuntu also ran out of RAM doing everyday tasks, indicating that 384 MB of RAM was inadequate. The review concluded "It was obvious I had already run out of RAM and was starting to use swap space. Considering I wasn't doing very much, this was rather disappointing

I wish there was a benchmark graph on these different set ups

it seems as debian minimal with xfce is lighter than ubuntu according to wikipedia post. ???

ubuntu minimal is lighter than netbook ubuntu?

will check out Linaro

---

### Post by mcduck on 2011-03-11
> **007casper said:**
> [http://en.wikipedia.org/wiki/Xubuntu](http://en.wikipedia.org/wiki/Xubuntu)


I wish there was a benchmark graph on these different set ups

it seems as debian minimal with xfce is lighter than ubuntu according to wikipedia post. ???

ubuntu minimal is lighter than netbook ubuntu?

will check out Linaro

Ubuntu minimal with XFCE is a lot lighter than Xubuntu is. ;)

Ubuntu Minimal on it's own is definitely lighter than Netbook Remix. Although it *is* just a CLI install, so it's pretty much up to what window manager/desktop environment and programs you choose to add to it. (I have a Ubuntu minimal + Openbox setup on one of my machines, it's using 43MB of RAM. With a desktop, pretty GTK apps and some compositing effects... I'd say that's pretty OK for such easy-to-setup lightweight system. :))

---

### Post by 007casper on 2011-03-13
I was going to try ubuntu minimal with xfce.  Then, came across this. [https://wiki.ubuntu.com/ARM/OMAPMaverickInstall](https://wiki.ubuntu.com/ARM/OMAPMaverickInstall)

I decided to give it a spin.  Unfortunatelly, I couldnt unmount the SD disk like the instructions.  Everytime, I would hit unmount from gui, it will unmount all the way, and it wont sit on the system.  It just would unmount completely.  I couldnt even access it through terminal by using sudo fdisk -ls.

So, I mounted it again, and checked on the terminal through fdisk -ls

the terminal showed the SD card.

entered > 
sudo sh -c 'zcat ./ubuntu-netbook-10.10-preinstalled-netbook-armel+omap4.img.gz >/dev/sdf'

it seemed like nothing is happening on the terminal. System monitor showed idle.  The toolbar process icon would also show idle. I moused over it, it would say 100%. what?

I went to SD card through gui, refresh.  It hanged a bit.

then I close the terminal.  Then, checked the sd card through gui.  Next thing you know I got bunch of files that looked encrypted.  They looked really strange.  These files had dates such as Tue 17 May 2050.  There was one file from 1983, 2009, the rest of the files were set in the future 2096,2103.

I tried to delete them.  Select all, delete.  Nope.  

Selected one, delete. Nope.

I went to the terminal fdisk -ls

The sd disked showed on the terminal.  Checked the processor icon on the top toolbar, it showed 100%.  Then, went to system > Administration > System monitor > Process -top gnome-system-monitor 10-12% 

weird?
```

cd /media/
ls
FC30-3DA9 (the sd card)
cd FC30-3DA9
ls
/media/FC30-3DA9$ ls
ls: cannot access &#8805;âï&#8730;&#9555;@&#9492;.÷&#9561;&#8805;: Input/output error
ls: cannot access æ39/æ&#9574;&#9632;.e&#9500;>: No such file or directory
ls: cannot access &#8734;&#8776;*&#966;}[&#9559;.S.: No such file or directory
ls: cannot access &#9566;&#8804;4{:&#9500;ü.&#9472;à2: Input/output error
t&#8359;;G/.&#9488;å\: No such file or directory
ls: cannot access Ä/U7&#9558;&#9579;s.ô&#937;&#948;: No such file or directory
ls: cannot access &#9566;+M&#9508;Åf£\.e&#8359;: Input/output error
ls: cannot access K&#8801;&#402;V4&#9568;&#9565;°.E&#9571;: Input/output error
ls: cannot access &#9573;&#9565;&#9571;ºiìh.¥;: Input/output error
ls: cannot access &#9559;&#8730;régsÿ.&#9484;vì: Input/output error
ls: cannot access %&#8801;&#9552;H.b9&#948;: Input/output error
ls: cannot access p` _&#9492;3.$&#9577;': Input/output error
ls: cannot access i6&#9555;ë¬·z@.&#9574;då: Input/output error
ls: cannot access &#9557;n&#9554;-&#9569;&#9488;[z.@c2: Input/output error
ls: cannot access &#937;¥Éó&#8745;d&#9560;&#9571;.M3: Input/output error
ls: cannot access 6&#9488;/&#9573;&#9564;.íê: No such file or directory
ls: cannot access &#9619;axvß%.»e: Input/output error
ls: cannot access én&#9532;èì[&#8730;.&#9568;&#915;&#9508;: Input/output error
ls: cannot access &#9632;&#9552;s:`.h¬: Input/output error
ls: cannot access q&#963;
                    zy&#9617;?d.&#9561;ò1: Input/output error
ls: cannot access ^Dò&#8801;Ñ&#9632;0&#8976;.&#9555;&#8729;&#937;: Input/output error
ls: cannot access e?æñ&#945;)(.&#9556;öe: Input/output error
ls: cannot access &#9472;j
ü&#9532;&#9616;&#9618;.kµA: Input/output error
ls: cannot access &#8730;àgïgu0l.&#9561;d: Input/output error
ls: cannot access rxà&#9554;óº.½&#8801;: Input/output error
ls: cannot access )&#9565;pC&#8993;&#9566;.4&#9570;3: Input/output error
ls: cannot access &#9571;'&#9567;ëbgê&#9571;.¼ë?: Input/output error
ls: cannot access &#9559;&#9568;[w&#8804;.&#9508;.: No such file or directory
ls: cannot access ws&#9552;&#9562;wú.9&#9552;ß: Input/output error
ls: cannot access /²=r&#9571;t&#9576;&#9565;.&#8319;&#9580;c: No such file or directory
: Input/output errorq4&#9579;&#9508;`&#9474;.&#9572;&#960;
ls: cannot access ÷Ü4k&#9492;&#8359;.&#9496;&#9576;&#964;: Input/output error
ls: cannot access ne&#9572;²&#9564;æq.&#9524;ö&#9496;: Input/output error
ls: cannot access «&#9577;%uw!#.f&#9567;B: Input/output error
ls: cannot access ïbE&#9555;&#9566;#&#9508;.@¼&#9562;: Input/output error
ls: cannot access /\+å«ç|é.
                           8G: No such file or directory
ls: cannot access 
&#8319;&#9608;&#8729;".3j&#9524;: Input/output error
ls: cannot access 5t&#9604;&#9556;&#9619;ay&#9488;.&#9577;,: Input/output error
ls: cannot access &#9617;&#8976;½ñ&#8804; +.ë<: Input/output error
ls: cannot access Æ&#9619;é+&#8992;&#9580;:ù.+&#937;T: Input/output error
ls: cannot access sùí&#9561;1&#9567;o.&#9618;b: Input/output error
ls: cannot access b¡läz_.&#8801;6u: Input/output error
ls: cannot access 6?ônl#ï.&#8729;c&#8804;: Input/output error
ls: cannot access &#8993;Zk&#966;>&#964;.µ': Input/output error
ls: cannot access 5&#949;ö&#9472;y&#9579;.0[ò: Input/output error
ls: cannot access &#9524;
%r&#9632;d&#9492;&#9474;.&#920;R&#9560;: Input/output error
ls: cannot access éñ?=&#9568;&#9575;&#949;.7s^: Input/output error
ls: cannot access &#9492;o>&#920;ê&#8992;9.&#9600;p: Input/output error
ls: cannot access &#9562;M-áR#ù.a&#9575;: Input/output error
ls: cannot access &#9474;3&#9560;è&#8804;&#8804;
                        &#9568;.&#937;cG: Input/output error
ls: cannot access à&#9508;ì&#9554;a&#934;.üè²: Input/output error
ls: cannot access &#8776;w°#+åô.ª¢): Input/output error
ls: cannot access &#9524;&#9632;.upù: Input/output error
tßry<'.&#9567;o£: Input/output error
ls: cannot access í&#9484;ß&#9554;V»±Z.&#8729;$Ç: Input/output error
ls: cannot access &#963;&#9561;&#966;;&#9496;&#9500;&#9618;.&#9532;æ: Input/output error
ls: cannot access ì&#9574;ë[&#8992;"&#8805;&#9569;./&#966;!: No such file or directory
ls: cannot access îù<&#8804;P&#9553;è.n: Input/output error
ls: cannot access (t&#9573;&#9600;&#9553;s&#920;.&#8805;m: Input/output error
ls: cannot access ì&#8776;&#9632;&#9571;&#9552;&#9563;¢.sâ): Input/output error
ls: cannot access &#8729;ô&#8729;&#915;è&#966;.v!: Input/output error
ls: cannot access îp*&#9574;&#9619;É&#8730;.VP: Input/output error
ls: cannot access ! >/1'.&#9567;}O: No such file or directory
ls: cannot access &#963;r&#402;ú\&#8729;&#9619;.>T: Input/output error
ls: cannot access &#8734;&#8319;u+e(µ.ü7: Input/output error
ls: cannot access à&#9500;µHC&#9484;5ë.vì<: Input/output error
ls: cannot access &#9574;&#964;ò&#9554;ª{&#948;4.&#9561;&#9565;8: Input/output error
ls: cannot access &#8992;ª&#9562;¬x&#9500;&#9484;0.x&#9524;&#8976;: Input/output error
ls: cannot access sù¢«&#9570;.)&#9575;
                           : Input/output error
ls: cannot access ^&#963;j&#9604;r&#8319;&#9632;.gvt: Input/output error
ls: cannot access &#9492;b&#915;&#9616;&#9516;6.&#402;0ï: Input/output error
ls: cannot access öÿuqe&#9577;&#8729;&#9500;.$&#934;Æ: Input/output error
ls: cannot access &#9578;&#963;&#9563;hzsl&#9578;.&&#9619;^: Input/output error
ls: cannot access &#915;&#9500;4&#8359;p&#9632;&#9488;.&#966;o&#960;: Input/output error
ls: cannot access w&#8805;d2hU&#9553;.ä;é: Input/output error
: Input/output error&#8319;6&#9558;é.c
ls: cannot access ñkü çò&#9579;.&&#402;s: Input/output error
ls: cannot accessÇ`&#8319;)<t.&#8730;&#9516;&#9496;: Input/output error
ls: cannot access v,K&#9566;&#948;&#9508;&#9558;.é
â: Input/output error
ls: cannot access &#9508;«nhæ&#9612;&#9474;.Üuè: Input/output error
ls: cannot access &#9562;ä&#9553;#:¥èN.'=.: No such file or directory
ls: cannot access ÷*&#9617;ä8&#8745;.H&#9488;ï: Input/output error
ls: cannot access &#9558;]/{k&#9560;&#8776;.&#920;&#9508;=: No such file or directory
ls: cannot access 2ù·W&#9573;:&#931;.@º&#8976;: Input/output error
ls: cannot access 	&#9632;µèö¢`&#9558;.52&#9552;: Input/output error
ls: cannot access j,u&#915;&#9553;r&#9569;.&#9496;": Input/output error
ls: cannot access &#966;	ä÷^a*µ.&#9575;h&#8745;: Input/output error
ls: cannot access 1X&#9573;?U.ft&#9574;: Input/output error
ls: cannot access &#9608;=o·&#963;ñ·.òá£: Input/output error
ls: cannot access &#9561;3åé&#9573;¼&#8730;.&#9573;&#9567;: Input/output error
ls: cannot access µ&#402;h\ez&#9574;e.&#9568;]&#9618;: Input/output error
".z&#9569;: Input/output error
ls: cannot access &#9558;Z;&#9612;&#8745;¬.(¿&#9566;: Input/output error
ls: cannot access  &#9474;&#945;7hz&#9563;.&#9559;j&#949;: Input/output error
ls: cannot access &#8992;&#9617;í&#945;&3x&#949;.&1&#8319;: Input/output error
ls: cannot access &#8359;b&#9558;&#402;¢Fb.&#9619;p7: Input/output error
ls: cannot access &#9552;fô¥0X1.&#9600;Q: Input/output error
ls: cannot access&#9563;&#9608;f&#9500;¥&#8992;&#8805;.{4&#931;: Input/output error
ls: cannot access &#9575;áé&#9558;5&#9600;&#8729;&#9579;.&#966;Æp: Input/output error
ls: cannot access °9`¢±&#9524;p&#9558;.&#9567;Y&#9488;: Input/output error
ls: cannot access \&#9532;&#8976;&#9608;&#9604;&#9574;&#920;&#9565;.&#9579;£ê: Input/output error
ls: cannot access &#8993;&#9617;x9
                      nw0.&#9558;e&#9619;: Input/output error
ls: cannot access T&#9524;lk·{&#9552;!.æê: Input/output error
ls: cannot access C]1Z&#9558;g. &#9579;v: Input/output error
ls: cannot access &#966;ô&#8730;óßüå.±&#9559;ó: Input/output error
ls: cannot access &#402;é.àº&#9571;&#9532;.&#915;&#9552;å: Input/output error
&#9557;w&#9570;t÷.9~:: Input/output error
ls: cannot access i&#966;aú&&#9576;r&#9557;.<&#8734;Q: Input/output error
ls: cannot access p@&#9576;&#8745;}&#9561;&#8993;.É4: Input/output error
ls: cannot access &#8319;AÄ&#9567;QC.ù&#9500;ù: Input/output error
ls: cannot access &&#9496;âmqc&#9492;q.&#402;#&#8730;: Input/output error
ls: cannot access &#9566;]*&#9558;öá&#9563;y.}w&: Input/output error
ls: cannot access û&#9554;
                    :o&#8805;5ù.èW: Input/output error
ls: cannot access &#963;&#8993;&#8745;&#9488;&#9569;Ñz.&#915;kZ: Input/output error
ls: cannot access »&#949;L¢V%/u&#9572;: No such file or directory
ls: cannot access &#8730;&#8319;tq_}k&#8359;.îuö: Input/output error
ls: cannot access b
                   r&#9579;æ>1.ä&#964;: Input/output error
ls: cannot access &#8804;jeiæ%&#9484;.w&#9569;&#402;: Input/output error
ls: cannot access &#9572;O}&#960;Ei&#966;._næ: Input/output error
ls: cannot access z&#9532;&#9516;&#9568;b&#9554;g.$vo: Input/output error
ls: cannot access &#9617;2r&#8992; dµ.ùH: Input/output error
ls: cannot access &#9554;èzx` #.ü·&#9563;: Input/output error
ls: cannot access v2)&#9568;0/&#9558;.&#8804;c: No such file or directory
ls: cannot access |&#9563;*ò*&#9608;a&#402;.ª&#9619;h: Input/output error
ls: cannot access &#9557;N&#934;
                      e8·.F~&#9632;: Input/output error
ls: cannot access w±ték.&#8729;&#966;8: Input/output error
ls: cannot access igpép.&#9558;&#915;&#920;: No such file or directory
ls: cannot access =&#9575;Ctc&#9472;&#9576;.&#8729;&#9492;: Input/output error
ls: cannot access &#9632;
                   ä&#9560;¢&#8319;Æ.¬}&#9574;: Input/output error
ls: cannot access e:&#9508;;¡)&#8804;&#8359;.&#8776;ä°: Input/output error
ls: cannot access _&#8730;iïÜ.÷&#9532;|: Input/output error
ls: cannot access &#8804;&#9574;o</¡$.&#8319;&#9608;: No such file or directory
ls: cannot access &#9565;&#9576;·f%1&#963;1.0s&#9576;: Input/output error
ls: cannot access ?tú&#9561;!>/,.]h: No such file or directory
ls: cannot access dc.
w&#964;: Input/output error
ls: cannot access &#8730;ôà"&#9572;ë&#9554;.`¢Å: Input/output error
ls: cannot access t&#9573;Ç
&#9578;&#9492;&#8729;J.fìê: Input/output error
ls: cannot access m&#937;¬&#9578;.òo*: Input/output error
ls: cannot access &#9575;»&#9578;o&#402;<ì£.&#8776;: Input/output error
ls: cannot access &#9555;n&#9474;g&#8976;mëï.&#9474;&#945;j: Input/output error
ls: cannot access b&#9569;&#9566;*	a.&#8319;ß0: Input/output error
ls: cannot access &#9508;b?«/e.º&#9612;g: No such file or directory
ls: cannot access &#8319;&#9555;&#8804;,6&#9576;&#9580;&#8776;.µè{: Input/output error
: No such file or directoryB
ls: cannot access \ê)&#8801;&#963;-yg.&#9532;o&#8729;: Input/output error
ls: cannot access Y&#9568;>MK&#9617;.&#948;[?: Input/output error
ls: cannot access Dw&#9563;&#931;3Y&#9632;T.[ÿ&#9492;: Input/output error
ls: cannot access íäkE&#9618;&#9618;m.º&#9553;Ö: Input/output error
ls: cannot access ubní&#8745;s&#9571;.&&#949;w: Input/output error
ls: cannot access &#8993;q&#9563;ßhc&#9619;.&#8993;º: Input/output error
ls: cannot access >&#8992;ca¡1vë.y: Input/output error
ls: cannot access 4z*=&#9559;">.l&#9570;: Input/output error
ls: cannot access ÿ&#9612;&#9474;&#9578;±
ñ.&#8745;d	: Input/output error
ls: cannot access w$e&#9574;àu&#9576;.`°
                            : Input/output error
ls: cannot access n²X&#945;U&ñ.dn: Input/output error
ls: cannot access ¿&#9474;¡.&#9612;dó: Input/output error
ls: cannot access '7&#8805;&#9570;&#9617;&#9567;£Ñ.K&#9569;W: Input/output error
ls: cannot access ñ&#8976;&#9619;å\£>.^&#9573;&#8319;: Input/output error
ls: cannot access lâî&#9580;ày&#9552;&#9569;.&#9619;3G: Input/output error
ls: cannot access &#9500;!&#9474;%&#9557;&#9572;rx.y9Æ: Input/output error
ls: cannot access &#9474;/â&#9554;äP&#9558;."&#9492;: No such file or directory
º&#9569;ö&#9577;.¼&#9560;&#9608;: Input/output error
ls: cannot access &#9616;gµ#re.é¬: Input/output error
ls: cannot access &#9564;k:&#9508;jG.é]&#966;: Input/output error
ls: cannot access wÄ*÷+L&#9561;.y5: Input/output error
ls: cannot access &#8319;1!&#9570;&#9557;'&#9524;.é&#8801;: Input/output error
ls: cannot access &#9555;&#9576;S&#9619;9.ó.Rü:: Input/output error
ls: cannot access tú0&#9484;fgm.y@ë: Input/output error
ls: cannot access &#9496;ázi&#9576;ñ.&#8745;&#9557;&#9565;: Input/output error
ls: cannot access dï84
                      d$".¿'Q: Input/output error
ls: cannot access &#963;a	ë&#963;m&#920;&#964;.&#8319;&#9568;Ñ: Input/output error
ls: cannot access $dxihu+.&#9474;»&#9579;: Input/output error
ls: cannot access 3&#8993;"h$z.&#9500;/µ: No such file or directory
ls: cannot access &#9569;72¡*2&.ûy&#9562;: Input/output error
ls: cannot access &#9565;&#402;&#9560;æj&#8730;]¢.x?&#8734;: Input/output error
ls: cannot access 	ï|
                          º¡.
                               &#9572;r: Input/output error
ls: cannot access åMuú&#9559;.&#966; &#963;: Input/output error
ls: cannot access s»?&#963;&#920;&#9561;qù.í;¿: Input/output error
ls: cannot access :9¥&#963;.*²: Input/output error
ls: cannot access {&#8776;!"ü&#9492;.&#945;&#9569;: Input/output error
ls: cannot access LC> ±N&#8730;.ï5&#8359;: Input/output error
ls: cannot access )Ä&#8319;&#8805;B&#9616;&#9563;./: No such file or directory
ls: cannot access aóq&#9488;&#9617;&#9552;.hi: Input/output error
ls: cannot access &#9558;çj&#9632;&#945;&#966;@.&#9557;Tx: Input/output error
ls: cannot access x&#9516;&#9561;@zm\.&#9563;#&#9496;: Input/output error
.s: cannot access &#9576;@&#966;&#9578;=¥
 ñ&#8734;: Input/output error
ls: cannot access &#8976;&#9563;&#9488;;2&#915;&#9604;2.8&#9572;&#9612;: Input/output error
ls: cannot access &#9562;é&#960;&#9608;&#9569;¢?.(i: Input/output error
ls: cannot access w2&#9564;ñä3&#8801;&#9578;.ó¬¢: Input/output error
ls: cannot access &#8993;üX&#8804;ôKH.¬Ö&#9524;: Input/output error
ls: cannot access &#9558;
&#9565;pñoò.Æí: Input/output error
ls: cannot access  &#9532;·&#9604;)+&#9500;.	«í: Input/output error
ls: cannot access ¬&#9564;{gì&#9472;V&#949;.&#915;R^: Input/output error
ls: cannot access ?&#9562;&#9524;&#402;&#966;J2].¬&#9500;: Input/output error
ls: cannot access vD'&#9561;b.ê&#9608;&#9566;: Input/output error
: Input/output error
ls: cannot access G&#9573;&#9579;ç°&#964;.°3.: No such file or directory
ls: cannot access &#8804;P&#9500;éo&#9554;1.rd&#9524;: Input/output error
ls: cannot access ¬&[]-~+	.(>: Input/output error
ls: cannot access åm(l9&#9559;tk.¥âÑ: Input/output error
ls: cannot access&#8359;&#8805;ov&#402;,.t: Input/output error
ls: cannot access &#9553;&#9568;ß&#9575;,eò.": Input/output error
ls: cannot access &#9553;&#9563;&#8804;&#963;\&#8734;ç.mvd: Input/output error
ls: cannot access &#8729;[ª6ñ&#9565;&#9578;&#9560;.&#966;£: Input/output error
ls: cannot access &#9580;*xäÿéD².: Input/output error
ls: cannot access iåe
                     ±&#9567;wö.é?ù: Input/output error
ls: cannot access 3&#8801;%&#9554;xæ?P.n/a: No such file or directory
ls: cannot access &#9555;Ñ&#9618;#&#8730;&#9564;&#934;y.v^: Input/output error
ls: cannot access t&#9496;&&#9573;ä`ù.¬&#8319;1: Input/output error
ls: cannot access 5DÆ÷&#9612;G.&#8805;&#402;Ü: Input/output error
ls: cannot access &#9552;v#*/&#9561;.&#9577;·ù: No such file or directory
ls: cannot access &#9616;&#9552;&#8993;&#9616;&#8976;&#8801;`.&#9492;&#945;: Input/output error
ls: cannot access ±&#9568;kô&#9524;cs&.&#9570;&#8729;: Input/output error
ls: cannot access q&#9484;&#402;&#9492;ù»ó.gà: Input/output error
ls: cannot access µ&#9608;&#964;
²t/.+n&#8976;: No such file or directory
ls: cannot access &#8359;:z)°~uë.&#9572;&#8729;: Input/output error
ls: cannot access ¿	«M&#945;q&#9565;.&#9567;: Input/output error
ls: cannot access &#964;+&#9532;;
a.-|Z: Input/output error
ls: cannot access ¼&#9516;D¥].yt«: Input/output error
ls: cannot access &#9484;&#9573;&#9566;ófICê.&#8734;·*: Input/output error
ls: cannot access &#9569;£Ç&#9580;&#9580;&#8729;&#9570;2.&#9532;àn: Input/output error
ls: cannot access &#8359;&#8993;íño£î&#9558;.w
                            &#9575;: Input/output error
&#9616;B: Input/output error&#8359;+&#9574;¡.
ls: cannot access L;Éö&#9532;²&#9564;.@&#9612;: Input/output error
ls: cannot access z&#9565;&#9579;{9&#949;/&#949;.ûá: No such file or directory
ls: cannot access &#9532;&#934;îû÷#å.&#964;&#8729;&#9516;: Input/output error
ls: cannot access &#9632;"6²YNÄ.w&#9566;&#9555;: Input/output error
ls: cannot access æ&#8804;&ä&#9565;&#402;a£.g£<: Input/output error
ls: cannot access *ì0c&#8805;æ&#8976;.&#9484;&#402;: Input/output error
ls: cannot access &#9516;w_&#9556;&#9632;ß_n.
                           z&#9557;: Input/output error
ls: cannot access &#9579;rî^@í.&#9566;&#9579;&#9574;: Input/output error
ls: cannot access &#9484;YäO¿¼h.p&#9571;
                            : Input/output error
ls: cannot access z+&#8801;e«.é,: Input/output error
&#9632;&#9608;: Input/output error &#8729;(1.
ls: cannot access &#9579;
&#964;YPm.ócs: Input/output error
ls: cannot access &#9580;ó±-£Bô(.\Æq: Input/output error
ls: cannot access &#9516;#b&#9608;»
                        &#9532;.E°5: Input/output error
ls: cannot access &#9508;pó&#9532;0æ.&#9508;&#9484;: Input/output error
ls: cannot access o&#9616;çï&#8730;l<.r:>: Input/output error
ls: cannot access ¢&#8776;&#9618;v&#8359;&#9557;g.&#9568;&#9555;²: Input/output error
ls: cannot access 2&#9472;k^ikar.s=&#9561;: Input/output error
ls: cannot access &#8976;&#931;N&#8776;&#9524;ül.r&#8319;&#8359;: Input/output error
ls: cannot access /ü8¢'&#8319;ä&#9578;. &#9608;t: No such file or directory
ls: cannot access &#9557;&#402;&#934;!&#9532;&#8734;6.û&#9559;w: Input/output error
ls: cannot access &#8801;IZ84»&#9600;.&#963;Y@: Input/output error
ls: cannot access &#9578;ï$&#963;&#9577; .f>: Input/output error
ls: cannot access hò'[½&#9616;&#9488;o.&#9508;&#8804;n: Input/output error
ls: cannot access &#966;=èh0
                       .æ&#945;é: Input/output error
ls: cannot access &#9560;&#9562;&#9554;.ÿº*: Input/output error
ls: cannot access x½u&#9632;ñsi&#9574;.*0&#9600;: Input/output error
ls: cannot access &#9563;.&#8730;w&#9500;	=.3: Input/output error
ls: cannot access <&#9571;â/&#8359;&#9580;.äê: No such file or directory
ls: cannot access j»&#920;&#964;nët[.&#949;: Input/output error
ls: cannot access åßeh&#9573;I.q#: Input/output error
ls: cannot access &#8319;/&#8801;&#948;åéo.5t&#920;: No such file or directory
ls: cannot access &#964;óå&#9555;[è&#402;5.?ò: Input/output error
ls: cannot access &#9578;;&#9560;&#9580;òÇ&#9618;.[: Input/output error
¬&[]-~+?.?(>  á?@&#9553;@&#9580;&#8734;¢.&#9600;ºC  i6&#9555;ë¬·z@.&#9574;då  &#9572;O}&#960;?Ei&#966;._næ  &#9516;w_&#9556;&#9632;ß_n.?z&#9557;
&#9632;??&#8776;&#9568;&#9580;(&#9612;. ?&#9608;  aóq&#9488;&#9617;&#9552;??.hi?  íæéü_?ä°.?ßf  &#9608;=o·&#963;ñ?·.òá£  ws&#9552;&#9562;wú??.9&#9552;ß
?.+'&#9472;         a&#9500;?ôs&#9556;+7."¿&#960;  iåe?±&#9567;wö.é?ù  |&#9563;*ò*&#9608;a&#402;.ª&#9619;h  ?&#9557;?w&#9570;t÷?.9~:
¼à}xp??&#937;.lg?  &#9500;'Äô&#8804;&#9554;?".z&#9569;?  íäkE&#9618;?&#9618;m.º&#9553;Ö  p?` _&#9492;3.$&#9577;'   w±t???ék.&#8729;&#966;8
??¼?&#9516;D¥].yt«  ?ªR&#937;ë&#9474;V&#8730;.&#9576;&#9579;?  ìª·X&#9472;&#9600;&#9565;].?tÜ  p8j&#9559;&#9516;&#9573;0n.ªtº  WYEÅåJä&#9474;.FN&#9608;
&#8319;&#8976;??&#9604;0&#9571;E.&#9632;&#9577;?  åße?h?&#9573;I.q?#  ïbE&#9555;&#9566;#?&#9508;.@¼&#9562;  )&#9565;pC?&#8993;&#9566;?.4&#9570;3  w£&#9560;&#963;ë&#8730;&#9560;ñ.&#9566;&#8992;&#9572;
&#9617;&#8976;½ñ?&#8804; +.ë<?  äß}r;D&#9558;?.·34  ìç&#9496;6&#9612;&#934;&æ.&#9574;ì?  p@&#9576;&#8745;?}&#9561;&#8993;.É4?  W&#934;IA <?¢.&#9560;&#9574;?
¼?\ó&#8805;&#966;f*.f&#9571;&#8729;  Ä/U7?&#9558;&#9579;s.ô&#937;&#948;  ïd&#9580;i2·rñ.&#8729;&#964;?  &#8804;P&#9500;é?o&#9554;1.rd&#9524;  x½u&#9632;ñsi&#9574;.*0&#9600;
¼ü?%°?&#9561;¢.&#9564;?Ü  &#8993;åu?=¿$l.hê?  ï[êà &#8993;&#9532;û.?&#949;&#8359;  \p?&#8992;î5&#9600;¢.&#9575;ôí  &#8993;&#9617;x9?nw0.&#9558;e&#9619;
&#8319;1!&#9570;&#9557;?'&#9524;.?é&#8801;  `áù&#9532;&#949;&#8745;_?.??q  ì&#9574;ë[&#8992;"&#8805;&#9569;./&#966;!  ?;p&#8805;LÇ?ß.?g1  &#9579;x&#9555;ô&#8730;&#8805;&#8801;\.^&#8805;&#9524;
! >?/1'.&#9567;}O   a&#9616;&#8319;v&#8993;dû4.&#9612;h?  i?g/?pép.&#9558;&#915;&#920;  pm'ë&#915;ä&#9570;&#966;. &#9619;&#9558;  ?x?U&#931;&#9600;°I.½We
&#8745;1ß?&#9568;&#9632;&#9524;h.m*&#949;  &#8729;åvïx#i..¥Fä  &#9532;i&#9524;&#9578;ïo&#9572;ü.ÿ&#9604;&#920;  &#9558;?&#9565;pñoò?.Æí?  &#9579;x?X?»?&#948;.e?m
&#9618;1ùá?oå&#963;.v&#9569;&#9568;  &#8992;ª&#9562;¬x&#9500;&#9484;0.x&#9524;&#8976;  _&#8730;?iï??Ü.÷&#9532;|  &#9508;?pó&#9532;0æ?.&#9508;&#9484;?  x&#9516;&#9561;@z?m\.&#9563;#&#9496;
1X&#9573;?U.ft&#9574;     ?&#9619;axvß%?.»e?  í#°k?ºL].c -  &#9492;p??üî:&#9532;.&#949;&#960;u  [&#9573;&#9472;XZm??.?{«
&#9618;²°&#9579;\???.«&#9561;è  &#9496;á??zi&#9576;ñ.&#8745;&#9557;&#9565;  &#8359;&#8993;íño£î&#9558;.w?&#9575;  ?q@1?&#8805;*g.&#8745;?&#9564;  x&#9565;µ&#9496;*h^?.&#9580;\?
2é±¥&#8359;+&#9574;¡.?&#9616;B  ?å&#915;±&#8804;&#9555;&#9472;º.&#9488;&#9474;x  I&#9565;&#8319;&#9616;&#9576;?&#9561;&#9562;.&#9617;Öá  #?Q5&#8776;&#9567;&#9571;&#9574;.?wñ  y?;?&#8730;?}2.?jä
²g            à&#9552;&#948;té?d+.?&#9567;?  ?ï|???º¡.?&#9572;r  ,q?c&#9632;¥??.?ä?  µy?&#9619;Æ?±c.æ&#920;$
2&#9472;k^ikar.s=&#9561;  å&#949;&#9560;É?µjQ.4^ä  îp*&#9574;?&#9619;É&#8730;.VP?  &#9600;q(?(in?.è'h  &#9484;YäO¿¼?h.p&#9571;?
?2&#9562;&#9484;º&#9556;t&#9492;.â°-  &#402;&#9632;a`?&#9608;&#9618;?.&#963;ä¥  &#9608;Iq4&#9579;&#9508;`&#9474;.&#9572;&#960;?  &#8993;q&#9563;ßh?c&#9619;.&#8993;?º  Y?&#9568;>?MK&#9617;.&#948;[?
&#9617;2r&#8992; dµ?.?ùH  @a&#964;â¥'?&#8359;.&#9575;m&#9564;  ì?&#8776;&#9632;&#9571;&#9552;&#9563;¢.sâ)  ?q&#9484;&#402;&#9492;ù»ó.g?à  ?ÿ&#9612;&#9474;&#9578;±?ñ.&#8745;d?
/²=r&#9571;t&#9576;&#9565;.&#8319;&#9580;c  a&#9532;&#9571;&#9579;-£¿&#937;.=u&#9632;  )&#9496;îs&#9580;è&#9561;û.V?L  q&#963;?zy&#9617;?d.&#9561;ò1  +&#9571;y?º&#9569;ö&#9577;.¼&#9560;&#9608;
²t&#9524;&#8804;??s&#9566;.&#9554;º&#9612;  ±«b~7?&#9488;&#9564;.&#9474;9?  í&#9484;ß&#9554;V»±Z.&#8729;$Ç  &#9524;?%r&#9632;d&#9492;&#9474;.&#920;R&#9560;  ?¡ÿ&#9484;&#9566;&#9552;&#937;£.2^á
&#9571;]?²ù¼&#9579;ö.êm&#9552;  B&#9574;;â.&#964;&#9577;&#948;      &#8734;#&#9568;&#9576;&#9569;?^I.Uà&#964;  &#9559;&#8730;rég?sÿ.&#9484;vì  ?y?*&#8776;#&#9562;&#9474;.¼&#9552;ª
2ù?·W&#9573;:&#931;.@º&#8976;  &#9516;#?b&#9608;»?&#9532;.E°5  ?îù<&#8804;P&#9553;è.??n  &#9532;&#9524;&#9496;Réq?&#9563;.&#9561;«4  ?&#9558;Z;&#9612;&#8745;?¬.(¿&#9566;
&#8976;&#9563;&#9488;;2&#915;&#9604;2.8&#9572;&#9612;  &#9508;b???«/e.º&#9612;g  %ivî¬e?&#9612;.°°z  &#8745;R:G·}'P.&#9568;;h  z&#9565;&#9579;{9&#949;/&#949;.ûá?
)<²*?&#9616;&#9566;&#963;.ù?ö  &#8359;b&#9558;&#402;¢?Fb.&#9619;p7  &#8801;IZ84»?&#9600;.&#963;Y@  &#9579;?rî^?@í.&#9566;&#9579;&#9574;  z?&#9532;&#9516;&#9568;b&#9554;g.$vo
&#9559;3åç.·¡&#915;      b¡l?ä?z_.&#8801;6u  &#8992;&#9617;í&#945;&3x&#949;.&1&#8319;  rr&#9496;?&#8776;?»&#963;..?&#9472;  z+?&#8801;e?«?.é?,
&#9561;3åé&#9573;?¼&#8730;.&#9573;?&#9567;  b?ñ?&#8805;?+&#8734;.&#9565;&#9579;?  &#9578;?ï$&#963;&#9577; ?.f>?  RÜ?9PlL?.9ñ?  &#8993;??Zk&#966;>&#964;.µ?'
&#9474;3&#9560;è&#8804;&#8804;?&#9568;.&#937;cG  b??r&#9579;æ>1.?ä&#964;  i&#966;aú&&#9576;r&#9557;.<&#8734;Q  >}?Rùæ>&#915;.*x&#9563;  "z&#8976;o&#8805;&#9557;#2.·sa
?3&#8993;"h?$z.&#9500;/µ  &#9492;b&#915;&#9616;&#9516;?6?.&#402;0ï  &#9619;í&#8359;&#934;ûÇ7&#8729;.?çp  R&#9564;wì?É&#9532;:.nH&#9472;  <zö&#9572;ò&#8745;·u.¿Å¿
??&#8319;&#9608;?&#8729;"?.3j&#9524;  b&#9569;&#9566;?*??a.&#8319;ß0  ?&#8804;jeiæ%&#9484;.w&#9569;&#402;  rxà?&#9554;?óº.?½&#8801;  ?ZR[<&#9575;½%.&#9554;?&#9565;
3ö&#9566;&#9532;?h&#8776;&#9618;.??,  C]1Z&#9558;gè?. &#9579;v  j\[ó~9&#937;&#9580;.?&#9617;?  &#9500;!&#9474;%&#9557;&#9572;rx.y9Æ  &#8359;:z)°~uë.?&#9572;&#8729;
3&#8801;%&#9554;xæ?P.n/a  &#9569;£Ç&#9580;&#9580;&#8729;&#9570;2.&#9532;àn  &#9472;j??ü&#9532;&#9616;&#9618;.kµA  r!&#9580;ÿ&#9612;1&#966;&#948;.MSº  ?&#9616;&#9552;&#8993;&#9616;&#8976;&#8801;`.&#9492;&#945;?
3&#931;£?Öì²?.ß4·  >&#8992;ca¡1vë.y    j,u?&#915;&#9553;r&#9569;.?&#9496;"  S°??2&#9570;~&#9573;.k&#934;&#9516;  %&#945;¼í?$½].&#9616;¢ü
??4å?)»á.ôz&#8319;  ·C?«æ¬&#9612;?.:??  j»&#920;&#964;nët[.?&#949;?  S7?¬??N°.f??   &#9474;&#945;?7hz&#9563;.&#9559;j&#949;
4f*gXE«í.q+w  c?&#9616;gµ#re.?é¬  &#9484;?K&#9561;½?%&#9568;. é&#9572;  &#9555;&#9576;S&#9619;9.ó?.Rü:  &#945;b&#9524;slú&#9618;¢.j&#937;n
?&#9566;&#8804;4{:&#9500;ü.&#9472;à2  ÇH??&#8734;]N!.k&#9575;&#966;  ?&#9564;?k:&#9508;jG.é]&#966;  &#9632;&#9552;¡??s:`.h¬?  &#9566;&#945;&#9555;e??#&#9532;.&#9568;&#9516;?
4z*?=&#9559;">.l&#9570;?  &#9500;c&#8801;&#9562;?·i}.÷&#9474;0  ¥>&#9568;&#402;&#9484;?Km.ºQ?  !&#9575;sL?ÖY?.?bå  &#945;·Ñ9&#9524;xÑ?.2^)
4&#945;&#8804;?&#9559;äU@.8&#8734;v  &#9558;çj?&#9632;&#945;&#966;@.&#9557;Tx  'k!n°npw.&#934;;h  &#9562;sö&#8319;ä&#9560;æ&#9564;.&#8992;FM  &#945;&#945;?ñçr&#964;ª.(y&#945;
±5&#9472;æ{???.6m&#9575;  ?Ç`&#8319;)?<t.&#8730;&#9516;&#9496;  ±&#9568;kô&#9524;cs&.?&#9570;&#8729;  &#9553;?&#9568;ß&#9575;,eò."¥?  ?&#915;&#9500;4&#8359;p&#9632;&#9488;.&#966;o&#960;
5DÆ÷&#9612;?G?.&#8805;&#402;Ü  =&#9575;Ctc&#9472;?&#9576;.&#8729;?&#9492;  k?&#9580;UMJÇ*.?öæ  ?sù¢«&#9570;á?.)&#9575;?  &#915;E&#8319;/&#9580;?\?.?B?
5t&#9604;&#9556;&#9619;ay&#9488;.&#9577;?,  Ç??t&#8359;;G/.&#9488;å\  K&#8801;&#402;V4&#9568;&#9565;°.?E&#9571;  ¡süáv&#9572;bo.&#9580;¼:  ?&#915;ï5&#9560;&#8729; o.&#9618;ì&#915;
5&#949;??ö&#9472;y&#9579;.0[ò  &#9574;`·??¡?ç.&#964;\r  ?K&#9567;yå&#931;\º.&#8319;!?  sùí&#9561;1?&#9567;o.&#9618;?b  &#915;w?&#9554;m3&#9559;f
&#9632;"6²YN?Ä.w&#9566;&#9555;  ?{?c&#9569;;&#937;.l4}   &#9558;]?/{k&#9560;&#8776;.&#920;&#9508;=  s»?&#963;&#920;&#9561;qù.í;¿  &#8319;?/&#8801;&#948;åéo.5t&#920;
&#8319;&#9555;&#8804;,6&#9576;&#9580;&#8776;.µè{  ?dc.?w&#964;       &#9508;?l"?æ@&#920;.&#963;jª  t7?&#8776;¥º?[.aè&#9608;  ¿?&#949;&#9496;¥&#9474;&#8729;Å.?ö&#9572;
"&#8993;?&#8319;?6&#9558;é.?c?  ?D?-GÆv&#9555;.gáµ  lâî&#9580;ày&#9552;&#9569;.&#9619;3G  t&#9496;&&#9573;ä?`ù.¬&#8319;1  &#9619;&#949;gf¡h&#9612;&#9608;.&#9576;x6
6+&#9557;&#8734; h&#9571;&#8805;.&#9575;:&#8805;  dï84?d$".¿'Q  "L±&#8729;&#8801;çJ;.(?¿  t&#9573;Ç?&#9578;&#9492;&#8729;J.fìê  »?&#949;L¢V%/.?u&#9572;
6&#9488;/??&#9573;?&#9564;.?íê  ¿&#9474;?¡.&#9612;dó      LC> ±N&#8730;?.ï5&#8359;  &#9569;\&#8776;tÇün&#9555;.&#9562;&#8729;&#9556;  ??\&#949;&#963;}??.&#931;¼¬
6?ônl#?ï.&#8729;c&#8804;  ^Dò&#8801;Ñ&#9632;0&#8976;.&#9555;&#8729;&#937;  L;Éö&#9532;?²&#9564;.@?&#9612;  tê2û&#9524;?ç?.0&#937;J  ?&#920;åûü&#8804;&#9604;?.?l¿
6&#8734;=&·ß*3.h?&#9573;  dtº&#966;u·&#9532;&#9560;.ue*  [lrhb&#9554;üq.*?<  T&#9524;lk·{&#9552;!.æê?  \&#9532;&#8976;&#9608;&#9604;&#9574;&#920;&#9565;.&#9579;£ê
6TT-&#8993;'k&#8734;.&#9573;&#8734;o  &#9600;d&#402;?ù?q].çom  ?luáº?Um.ñ&#9568;&#9632;  ?TN<½&#9516;&#9488;?.?&#8359;&#9573;  &#920;l&#9500;½lror.5?&#9555;
?&#9569;72¡*2&.ûy&#9562;  DU&#402;u?"&#963;°.&#9632;·?  &#9554;Lù?îP&#9559;?.^É&#9556;  &#8730;&#8319;tq_}k&#8359;.îuö  &#920;&#8745;&#9524;&#9472;ö&#9580;W&#8745;.²2x
7&#9568;c6po5î.?3>  ?D<w&#8734;&#9604;&#9554;&#8734;.&#8992;NB  &#9500;l&#9604;¬?:;&#9566;.&#934;ú?  &#8745; tr;(2&#937;.ö«&#8729;  &#960;¡)ªa&#8730;&#963;è.º&#8805;è
+&#9565;7&#8745;c?ó0.û&#9492;?  Dw&#9563;&#931;3Y&#9632;T.[ÿ&#9492;  &#9561;m&#9567;&#9553;?7ì&#9552;.&#8992;v&#9576;  &#9564;&#9566;t&#9560;)¬sº.æ#&#8805;  &#960;B&#9472;!|÷&#915;Ä.$í&#9559;
'7&#8805;&#9570;&#9617;&#9567;£Ñ.K&#9569;W  $dxihu?+.&#9474;»&#9579;  m&#8804;?å&#9556;&#8730;?ä.*61  &#9576;?tßry<'.&#9567;o£  ?&#960;'úwwåö.s?h
7º&#9579;ë&#8992;ä5ò.Rµ_  D&#949;ETJ?ws.?&#966;&#9573;  &#9566;+M&#9508;Åf£\.?e&#8359;  (?t&#9573;&#9600;&#9553;s&#920;.&#8805;?m  &#960;&#963;Z$?b[Ü.ï*&#9565;
?&#9576;&#9560;·7^p_.&#949;ª?  &&#9563;d&#963;ñ]\&#9618;.?Na  &#9562;M-áR#ù?.a&#9575;?  tú0&#9484;?fgm.y@ë  &#963;&#8776;&#9484;~&æï1.?n<
&#9492;<8&#9472;z&#9569;&#9572;&#9555;.S&#9565;&#934;  &#8729;«.&#9618;*ë        ¥m&#9558;&#9619;?aµ&#8776;.&#920;??  ?tú&#9561;!>/,.?]h  &#963;a?ë&#963;m&#920;&#964;.&#8319;&#9568;Ñ
&#9578;8&#9573;&#931;?äî&#8359;.,&#9569;%  &#9571;ë]{1kó&#949;.??|  mm?°&#9564;½¢?.ecu  &#9612;?$&#9574;t&#949;&#9524;s.&#9612;?n  &#9553;?&#9563;&#8804;&#963;\&#8734;ç.mvd
°9`¢±&#9524;p&#9558;.&#9567;Y&#9488;  &#9484;è?1L&#8804;e&#9554;.&#9604;:q  &#9516;?&#9577;?m&#9558;t?.&#9619;¢&#9570;  ?t&#9566;¿&#960;&#9579;?·.&#9600;(B  &#9578;&#963;&#9563;hzsl&#9578;.&&#9619;^
:9¥&#963;.*²?      e:&#9508;;¡)&#8804;&#8359;.&#8776;ä°  ¿?«M&#945;?q&#9565;.&#9567;??  \?u«&#9524;\,?.?}&#9558;  &#963;&#9567;&#9573;&#9472;?i?x.àq
&#9566;&#8734;.Å!½        ê?ª&#9608;a&#960;æÉ.?ªö  ?m??&#937;¬&#9578;?.òo*  &#8992;¿&#9553;?^&#9632;Ü?.&#9618;&#8729;2  ^&#963;j&#9604;r?&#8319;&#9632;.gvt
á&#9566;0?&#9556;&#9616;?&#9532;.e@?  é&#9571;?æ&#9564;44&#8319;.'5l  n?&#9575;&½hç?.?&#9577;_  ÷Ü4k??&#9492;&#8359;.&#9496;&#9576;&#964;  &#8976;&#931;N&#8776;&#9524;?ül.r&#8319;&#8359;
ä^1?&#937;&#9600;{p.H&#9604;&#9579;  e?æñ&#945;)(?.&#9556;öe  n²X&#945;U&ñ?.?dn  ??ú&#9552;?&#8976;&#9567;4.&#9578;p¡  ?&#963;&#8993;&#8745;&#9488;&#9569;Ñz.&#915;kZ
&#9563;&#9563;?å??²&#8729;.á<?  &#402;é.àº&#9571;&#9532;?.&#915;&#9552;å  n3buügf4.a]&#915;  /ü8¢'&#8319;ä&#9578;. &#9608;t  ?&#963;oêo?"ñ.²
;å3\p&#9578;n¬.e=ú  eåO?&#948;?&#9532;&#9579;.&#9617;&#8993;°  ñ&#8976;&#9619;å\£>?.^&#9573;&#8319;  &#9472;ü9&#9516;&#9612;?F&#9632;.?Æ&#9571;  &#963;?r&#402;ú\&#8729;&#9619;.>?T
á&#8734;¡5º¿t?.&#8734;fä  &#9571;'&#9567;ëbgê&#9571;.¼ë?  NA?fÿJc&#9572;.>p?  ub?ní&#8745;s&#9571;.&&#949;w  &#963;?t\ñ$?&#8993;.s ?
&#8729;[ª6ñ&#9565;&#9578;&#9560;.&#966;£?  ëd?&#9560;ß&#9564;ñå.é&#9559;î  ne&#9572;?²&#9564;æq.&#9524;ö&#9496;  üço^käû&#9532;.&#8801;&#9558;ë  ?&#963;&#963;æ&#9600;'&#9571;&#9555;.ô&#9556;$
÷*?&#9617;ä8?&#8745;.H&#9488;ï  &#8729;&#9552;èï?&#934;&#9600;&#9570;.c&#9508;r  &#9555;n&#9474;g&#8976;mëï.&#9474;&#945;j  &#8734;&#8319;?u+e(µ.ü7?  &#963;?&#9561;&#966;;&#9496;&#9500;&#9618;.&#9532;æ?
?ª8±&#915;ï&#9552;&#9557;.&#9576;&#9579;`  én&#9532;èì[&#8730;?.&#9568;&#915;&#9508;  ?&#9508;«nhæ&#9612;&#9474;.Üuè  u??¡f?c÷.g??  µ&#9608;&#964;?²t/?.+n&#8976;
?&#9574;&#9570;&#9474;&#9616;&#8734;à&#8729;.?&#8730;a  éñ?=&#9568;?&#9575;&#949;.7s^  n¡ï7Dè^².ÿ?&#8734;  &#9616;ù`j&#9600;&#8976;?n.Q9&#9567;  &#964;ä?ne¿?.&#9552;&#948;?
?&#8976;äÅ&#8776;&#8745;&#9604;¢.b&#964;9  ?&#9632;µèö¢`&#9558;.52&#9552;  ñkü çò&#9579;?.&&#402;s  &#9618;Ül&#9569;Q?&#948;*.&#963;&#920;?  ??&#964;+&#9532;;?a.-|Z
<&#9571;?â/&#8359;&#9580;?.?äê  &#402;ëRG?ÿ}ª.Æà&#9576;  ·?&#9556;??ñöJ.ä&#9632;&#8805;  &#9600;uñöo&#8993;½&#9474;.o&#9600;{  &#964;óå&#9555;[è&#402;5.?ò?
&#9632;?ä?&#9560;¢&#8319;Æ.¬}&#9574;  ét`2O0LU.&#9555;&#963;&#960;  ?ñQºSâ¬m.n}&#8729;  û&#9554;?:o&#8805;5ù.è?W  &#9574;&#964;ò&#9554;ª{&#948;4.&#9561;&#9565;8
&#9577;%âæ&#9508;&#966;p?.&#9576;&#9558;3  ?èUâ&#8734;l;k.eiA  &#9553;?n?R?&#8359;C.w&#9566;j  &#402;&#8804;ü?o&#8801;·º.(&#8801;ö  &#9579;??&#964;Y?Pm.ócs
å[?å&#8730;ìs&#9492;.?&#963;ï  &#9554;èzx` ?#.ü·&#9563;  ??n?&#9560;?&#9562;&#9554;.ÿº*  &#9524;&#9632;.upù        &#964;&#8734;&#960;dÉ&#9500;e&#9561;.&#8776;?&#9472;
&#9474;/â&#9554;äP&#9558;."&#9492;?   é&#945;d&#960;_öqj.&#9569;«è  &#9557;n&#9554;-&#9569;&#9488;[z.@c2  ?&#9552;?ü)&#9619;ûú.&#9496;?(  µ(???¡&#966;?.#?¢
&#8319;?AÄ&#9567;?QC.ù&#9500;ù  ê÷??&#9619;?&#920;ó.&#931;ü&#9559;  &#9557;?N&#934;?e8·.F~&#9632;  ?&#8729;¬_uw~(.5&#9564;E  ??&#966;-&#9555;5br.?Ö&
â&#9524;;#?áw^.i»ü  é[&#960;3&#9555;?cô.Lü&#945;  &#9555;Ñ&#9618;#&#8730;&#9564;&#934;y.v^?  «&#9577;%?uw!#.f&#9567;B  &#9557;&#402;?&#934;!&#9532;&#8734;6.û&#9559;w
)Ä&#8319;&#8805;?B&#9616;&#9563;./    &#9562;é&#960;&#9608;?&#9569;¢?.(i?  &#8804;&#9574;o</¡?$.?&#8319;&#9608;  ¥&#9559;ú£w[zl.«5&  &#966;?ä÷^a*µ.&#9575;h&#8745;
?å&#402;???&#9524;&#9616;.bdû  @ë&#960;&#9578;^ºnò.1m£  %&#8745;¿O7ï&#9600;7.?(l  &#8993;ü?X&#8804;ôKH.¬Ö&#9524;  &#934;?Å??I&#948;å.^d&#9569;
/\+å«ç|é.?8G  \ê)&#8801;&#963;-yg.&#9532;o&#8729;  &#8730;ôà"?&#9572;ë&#9554;.`¢Å  ±ú¬yºiqt.f?&#402;  &#966;?=èh0??.æ&#945;é
æ39/æ?&#9574;&#9632;.e&#9500;>  &#9565;&#9576;·f%1&#963;1.0s&#9576;  &#9566;]*&#9558;öá&#9563;y.}w&  ??{&#8776;!"ü&#9492;.&#945;?&#9569;  &#9532;&#934;?îû÷#å.&#964;&#8729;&#9516;
&#9575;áé&#9558;5&#9600;&#8729;&#9579;.&#966;Æp  ?&#9563;&#9608;f&#9500;¥&#8992;&#8805;.{4&#931;  &#9580;ó±-£Bô(.\Æq  ?û&#8804;&#9484;?&#964;&#9571;å.&#9565;&#8776;ë  ?&#9562;&#9524;&#402;&#966;J2].¬?&#9500;
æ&#8804;&ä&#9565;&#402;a£.g£<  f&#9612;&#9577;»ê&#949;ä'.&#8730;è=  &#9578;;&#9560;&#9580;ò?Ç&#9618;.?[?  V2}&#9508;&#9575;%,&#9617;.(??  &#9576;@&#966;&#9578;?=¥?.?ñ&#8734;
Æ&#9619;é+&#8992;&#9580;:ù.+&#937;T  &#9578;F&#9561;µM&#8993;)&#9555;.&#9557;?{  o&#9616;?çï&#8730;l<.r:>  v2?)&#9568;0/&#9558;.&#8804;c?  &#966;Ñ&#9559;?8?#|.ºY&#9579;
&#9516;æïæäh>a.é&#9564;?  &#9552;f?ô¥0X1.&#9600;?Q  &#9484;&#9573;&#9566;ófICê.&#8734;·*  %@!V`+D0.&#9556;l&#9612;  &#966;ô&#8730;?óßüå.±&#9559;ó
&#8359;æïö?&#9604;¢t.&#8359;ç|  ?fº1&#9578;Ü?&#402;.'üü  &#9575;»&#9578;o&#402;<ì£.&#8776;    v&#9632;?D'&#9561;?b.ê&#9608;&#9566;  &#966;?'p~wm&#9566;.(ùN
&#9565;&#402;&#9560;æj&#8730;]¢.x?&#8734;  &#9524;gæ&#8992;&#9552;q&#960;£.$&#9561;Ä  &#9573;&#9565;&#9571;ºiì?h.?¥;  ¢&#8776;&#9618;v&#8359;&#9557;g?.&#9568;&#9555;²  &#966;s&#9560;).7&#9616;*.8&#9560;r
&#9562;ä&#9553;#:¥èN.'=.  G&#9573;&#9579;ç°&#964;&#9557;?.°3.  ?&#9565;öìv:?Ñ.6?ÿ  v,K&#9566;&#948;?&#9508;&#9558;.é?â  &#9577;&#966;&#9492;uåü&#9632;&#8805;.&#9552;?G
àéû&#8992;?5?ñ.l&#9553;&#8745;  ggi&#9474;&#9577;µ2å.k_&#8976;  µ&#8745;.O÷&#9566;&#9574;K.ò&#9568;A  &#9552;v#*/&#9561;?.&#9577;·ù   &#966;ú?&#948;&#945;-&#9600;6.û?V
æ:ùz5&#8745;<?.?u2  g&#9474;iñ?:&#9474;&#9604;.?&#9574;&#9500;  &#9508;?¥?&#9496;ôñk.&#9563;?&#9524;  &#9492;V~&#9563;Y?ì?.&#9632;?F  &#966;&#9576;&#949;Æå&#934;?=.-&#9572;&#9574;
ª?&#9632;µg2é?.&#931;9!  ¬&#9564;{gì&#9472;V&#949;.&#915;R^  «ö&#8730;oâ&#948;¬?.@&#9612;æ  &#9559;?&#9568;?[w&#8804;?.?&#9508;.  &#966;&#963;srêjgê.7]>
&#9554;?&#8745;+áGîç.&#9552;ff  &#9474;g¬uw&#966;*«.2ü]  &#9560;O&#9616;&#8359;ÖH&#9571;K.&#9570;l?  w2&#9564;ñä3&#8801;&#9578;.ó¬¢  &#966;&#963;\¿ß%;r.&#8976;?&#9608;
&#8730;àgïgu0l.&#9561;?d  ??%&#8801;&#9552;H&#9575;?.b9&#948;  öt?½ââ&#9554;&#9566;.ó?&#9524;  &#9563;.&#8730;w&#9500;?=?.3??  &#937;¥Éó&#8745;d&#9560;&#9571;.M?3
&#9488;ah) &#8729;(1.?&#9632;&#9608;  µ&#402;h\ez&#9574;e.&#9568;]&#9618;  'ó¿£úª÷?.x5`  &#8776;w°?#+åô.ª¢)  &#937;.&#9555;ë&#964;
à&#9500;µHC&#9484;5ë.vì<  hiå&#9600;p¢&#9532;&#8992;.{??  ó?ûhô1ç&#963;.z&#9619;c  &#9617;%Wª&#9618;&#9556;ÜJ.&#8776;%}  *ì0c?&#8805;æ&#8976;.&#9484;&#402;?
&#8805;âï&#8730;&#9555;@&#9492;?.÷&#9561;&#8805;  hò'[½&#9616;&#9488;o.&#9508;&#8804;n  &#9474;òV?&#9484;&#9569;&#9488;&#402;.&#8805;9?  w?Ä*÷+L&#9561;.y5?  &#9580;*xäÿéD².ê??
à?\&#9508;ì&#9554;a&#934;.üè²  ?&#9558;>&#9572;höe&#9575;.&#9488;áT  ?&#8359;&#8805;ov?&#402;,.t??  w&#8805;d2h?U&#9553;.ä;é  &#8734;&#8776;*&#966;}?[&#9559;.S?.
åm(l9&#9559;tk.¥âÑ  ??&#9576;?h&#9578;&#9571;&#9575;.?y&#9565;  öÿuqe&#9577;&#8729;&#9500;.$&#934;Æ  w$?e&#9574;àu&#9576;.`°?
&&#9496;âmqc&#9492;q.&#402;#&#8730;  h&#9516;&#931;?&#402;Bñ&#9566;.:&#9578;$  &#8729;?ô&#8729;&#915;è?&#966;.?v!  wf&#964;ëå&#9554;1ÿ.ö&#948;&#915;
åM?u?ú&#9559;.&#966; &#963;    &#9532;·&#9604;?)+&#9500;.?«í  ¬o&#948;±?&#9618;¢ñ.Mt&#8805;  w*ï&#9575;C&#8801;zH.èÑ?
&#9524;]&#8804;[à£+N.ºvk  i0ègÅ?qº.&#8976;Nò  &#9492;o>&#920;?ê&#8992;9.?&#9600;p  W&#9566;r&#8976;ci&#9572;ó.&#9516;R¿
```

---

