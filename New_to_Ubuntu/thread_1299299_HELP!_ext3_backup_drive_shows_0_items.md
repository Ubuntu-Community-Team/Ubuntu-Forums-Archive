---
title: "HELP! ext3 backup drive shows 0 items"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by oldrocker99 on 2009-10-23
I formatted an external 1 GB Seagate drive using GPartEd as advised in the forums and backed up a bunch of stuff, including my home folder and all that was in it, to that drive. I have (after my %$&%&^% Toshiba laptop went to the shop) gone back to my desktop. The drive, which was perfectly readable in 8.10, opens with "0 items, 523 GB space free." That's how much free space was on the drive. 

The disk had been named /media/disk. Now it's named FFF4-D0EB and ls'ing it gives this:
oldrocker99@oldrocker99-desktop:~$ cd /media/FFF4-D0EB/
oldrocker99@oldrocker99-desktop:/media/FFF4-D0EB$ ls
ls: cannot access O&#9563;·Ö&#9557;Å&#9570;J.y»ï: Input/output error
ls: cannot access &#8730;à&#9492;9x.&#9553;&#9524;&#8745;: Input/output error
ls: cannot access ¬&#8734;ÿ4w&#945;b.¬&#8730;y: Input/output error
ls: cannot access }&#963;U[&#9532;A.&#8805;&#8976;": Input/output error
ls: cannot access r&#960;^ô&#9496;t&#9604;&#963;.&#963;dî: Input/output error
ls: cannot access ¬&#9571;R±&#9619;:.û: Input/output error
ls: cannot access &#9566;
&#9488;ul&#9571;o&#9559;.¼&#8993;%: Input/output error
ls: cannot access M&#9508;8&#8730;~&#931;¿&#8729;.]&: Input/output error
ÅU&#9618;è&#8804;: Input/output error
ls: cannot access å]&#9558; Çö.&#8801;&#9575;: Input/output error
ls: cannot access ë0h&#9617;y.
                         ªR: Input/output error
ls: cannot access *&#9577;&#8992;2kp.&#8976;8: Input/output error
ls: cannot access &#960;&#9552;ó"&#9579;&#9561;µé.&#9574;&#8805;: Input/output error
ls: cannot access W&#966;&#9555;½j&#9574;&#9573;.&#966;è: Input/output error
ls: cannot access &#937;½&#9567;yd&#9574;.&#9565;ç&#915;: Input/output error
ls: cannot access s&#9500;&#9616;åoù¥(.&#8359;&#9617;g: Input/output error
ls: cannot access ¬W UqYt.&#9570;&#9554;&#9558;: Input/output error
ls: cannot access KQô·&#8976;j.»: Input/output error
ls: cannot access uuîísg.&#949;#: Input/output error
ls: cannot access ¢rg!T(&ï.$&#9516;
: Input/output error
ls: cannot access P&#8730;&#9555;~_l.&#9570;	: Input/output error
ls: cannot access  &#8776;á*+ï&#8805;&#8319;.&#9576;x: Input/output error
ls: cannot access &#9568;°*&#9568;@d.&#9617;): Input/output error
ls: cannot access »&#9492;b&#9570;*æ&#9532;.&#9516;&#8992;: Input/output error
ls: cannot access ÖwW&#9552;ÑQ·.«&#948;w: Input/output error
ls: cannot access jx*u &#8801;¼.&#8359;3e: Input/output error
ls: cannot access 6_1
                     yg$û.æz&#8734;: Input/output error
ls: cannot access &#8776;Ü&#9608;Çª
                       üç.2&#8776;d: Input/output error
ls: cannot access Wí.ó~º&#9562;.{&#9577;}: Input/output error
ls: cannot access S&#9573;4°2ƒo].2så: Input/output error
ls: cannot access ä&#9578;ç°&#948;&#9563;&#8993;&#9564;.&#964;^s: Input/output error
ls: cannot access _jf]/&#9618;M.&#8729;}&#9619;: No such file or directory
ls: cannot access &#9559;?jà>fö..Rqµ: Input/output error
ls: cannot access °&#9564;]&#9559;8&#963;.&#9619;&#8730;&#9555;: Input/output error
ls: cannot access [email]b@²z&#9569;.BU[/email]¬: No such file or directory
ls: cannot access =&#920;k&#9488;_OC).ê[: Input/output error
ls: cannot access ÿi&#9552;'&#960;c¢>.y&#9492;ª: Input/output error
ls: cannot access &#9573;{&#9555;p
                      s&#9572;.é&#9524;: Input/output error
ls: cannot access u0_os&#9612;z.m0ú: Input/output error
ls: cannot access ö&#9532;es&#9616;&#915;.&#9576;âò: Input/output error
ls: cannot access g&#8804;Yt&#8745;]x.÷&#9568;é: Input/output error
ls: cannot access &#8992;²y)&_&#9561;&#8359;.&#9496;&#9573;: Input/output error
ls: cannot access oæ«&#9516;&#8801;&#937;ñ.,&#9554;
                            : Input/output error
ls: cannot access «rk¼·û&#931;.&#8976;#ú: Input/output error
ls: cannot access &#963;:f&#9556;&#963;&#9618;&#9632;=&#9604;&#945;: Input/output error
ls: cannot access &#8359;&#8805;æ±&#9612;)^.j&	: Input/output error
.&#8804;&#9600;&#8319;: Input/output errorc
ls: cannot access q/&#9568;8fm&#8804;&#8745;.y&#8776;: No such file or directory
ls: cannot access 
dRh&#8804;&#9570;R./jy: No such file or directory
ls: cannot access ü'¥`ß±.&#8801;&#937;: Input/output error
ls: cannot access &#9496;&#9560;j|ä&#937;i.¥2: Input/output error
ls: cannot access Ö£äÅm&#931;
                         .$: Input/output error
ls: cannot access Sñ:&#9577;&#9564;&#931;w&#8730;.&#9500;3µ: Input/output error
ls: cannot access &#9616;&#9553;ie&#9600;&#945;f.á: Input/output error
ls: cannot access j&#9524;
                    êüß0*.·y: Input/output error
ls: cannot access &#963;&#9573;@o&#9516;á.&#8319;vq: Input/output error
ls: cannot access T&#915;çCNT@.&#9570;¡: Input/output error
ls: cannot access ò&#9492;&#9554;MF&#964;.&#9558;: Input/output error
ls: cannot access &#945;%Q&#9559;îGM.(&#915;&#9572;: Input/output error
ls: cannot access &#8804;pio/b&#8805;..áê: No such file or directory
&. (/: No such file or directory
ls: cannot access í@ß3ç&#9570;S.}&#9568;0: Input/output error
ls: cannot access ½&#9568;¢²hj.&#8776;&#9554;¿: Input/output error
ls: cannot access (°~>ñ&#963;ß
                         .&#9563;X=: Input/output error
ls: cannot access &#9576;I&#8745;x&#9492;H.&#9580;&#8976;&#9492;: Input/output error
ls: cannot access &#9570;&#8776;æùù&#9619;:ƒ.P&#9552;&#8319;: Input/output error
ls: cannot access &#9496;qc÷&#9552;&#9472;&#9552;
.!&#9492;: Input/output error
ls: cannot access såpÿ(9&#9552;}.&#8992;ªa: Input/output error
ls: cannot access Yxå/5&#9618;&#966;.&#948;&#9560;&#9617;: No such file or directory
ls: cannot access ä»lìi&#9579;ë. X&#9488;: Input/output error
ls: cannot access Q&#920;¬zST$Ç&#9492;: Input/output error
ls: cannot access FçFA?&#8804;q.&#9579;&#9565;&#8776;: Input/output error
ls: cannot access &#9496;c5å?	ü&#8801;.&#9563;?: Input/output error
ls: cannot access ±3ö.a: Input/output error
ls: cannot access ½çA!(&#931;UB.é&#9516;B: Input/output error
ls: cannot access y¬8áäì<.
                           &#8729;: Input/output error
âæ&#915;@<&#964;.Qa: Input/output error
&#9564;&#945;.ÿ&#9616;&#8801;: Input/output error
ls: cannot access ñ0Ppê&#8729;&#9472;.&#920;ñ&#9484;: Input/output error
ls: cannot access &#9472;á0 &#9559;&#9616;./: No such file or directory
ls: cannot access ¬wdë&#9472;.u&#9600;ñ: Input/output error
ls: cannot access ß£1&#9563;&#9571;.çé: Input/output error
&#9488;ÿ&#8729;Ö&#937;&#8993;.k¼: Input/output error
ls: cannot access &#9579;&#920;°á&#920;½2&#9552;.pt: Input/output error
ls: cannot access &#9571;j&#9524;a£(g).&#920;·z: Input/output error
0&#9565;.{&#9488;: Input/output error
ls: cannot access &#9557;&#8992;&#9484;é1&#9556;e.:·d: Input/output error
ls: cannot access [&#9566;&#9564;Q&#920;&#9574;ÿ&#9600;.&#9488;ò9: Input/output error
ls: cannot access &#920;&#8993;t*ô÷7.%&#9632;{: Input/output error
ls: cannot access ê=BaD&#9571;T.µñ: Input/output error
ls: cannot access ób&#915;&#9558;&#9572;a&#9572;.&#9579;é: Input/output error
ls: cannot access 8&#9600;Q8H	.
                                  &#8993;: Input/output error
ls: cannot access &#8805;Å&#9474;&#9578;ñ*¿.úü&#9492;: Input/output error
ls: cannot access y&#9600;&#9575;g&#945;&#9516;·(.#Wx: Input/output error
ls: cannot access °±{¿
#ÅÄ.Åäv: Input/output error
ls: cannot access m,&#8359;p&#937;^z&#915;.&#937;lt: Input/output error
ls: cannot access ö&#8801;H(¿{.&#9632;&#9560;: Input/output error
ls: cannot access #Q&#9558;é`9=&#920;.M.Ä: Input/output error
ls: cannot access 	¥îç&#960;'&#9612;%.&#8319;&#948;: Input/output error
ls: cannot access &#8993;3&#9570;f&#9575;&#9496;b(.&#8729;d&#9608;: Input/output error
ls: cannot access ¬ó0öü.&#9576;(: Input/output error
ls: cannot access {&#963;x&#9557;

                      .3»: Input/output error
ls: cannot access 6#&#9524;&#9524;&#9484;|.` x: Input/output error
ls: cannot access  t&#963;&#9573;&#9524;.&#9616;: Input/output error
ls: cannot access cö*\L&#9632;.&#9559;C0: Input/output error
&#9560;Ç.&#8729;$: Input/output error
ls: cannot access ^&#8993;&#9472;j
                       Äò.&#9500;&#9508;&#9508;: Input/output error
ls: cannot access @gÿéæ&#9580;p&#945;.ù&#9569;1: Input/output error
ls: cannot access 7km&#9573;vkfü.x/&#931;: No such file or directory
ls: cannot access &#9567;&#9562;ä &#9554;ùî.ô-.: No such file or directory
ls: cannot access :?ë9W"J_.SMZ: Input/output error
ls: cannot access &#9562;\%¬l&#9488;&#9492;.h&#9565;¢: Input/output error
ls: cannot accessï-áº«.~ú&#8805;: Input/output error
ls: cannot access ª«@¢K~&#9562;
                         .&#9532;HI: Input/output error
ls: cannot access o<Æ&#9574;IÖl.co8: Input/output error
ls: cannot access &#915;n8&#8729;jq.e
                            f: Input/output error
ls: cannot access &#9557;hë;*&#9559;äá.w&#9577;?: Input/output error
ls: cannot access ùr&#9557;&#966;&#9557;n.u: Input/output error
ls: cannot access &#8993;qköùg¬.&#937;+v: Input/output error
ls: cannot access ]é&#9600;&#9567;&#9557;Å`é.l(&#9564;: Input/output error
ls: cannot access &#9575;&#9574;a&#915;d&#9617;æ.8¡&#966;: Input/output error
ls: cannot access y¢uvé&#9563;ï.&#9618;&#9569;`: Input/output error
½&#9568;¢²hj??.&#8776;&#9554;¿  ¢á&#9484;&#9484;&#8729;tl&#8745;.ºyz  &#9616;&#9553;i?e&#9600;&#945;f.á?   ?oy&#9560;ë?ñü.ÿ&#9567;å  W&??9ß&#931;&#948;.±_¼
½çA!(&#931;UB.é&#9516;B  &#8745;&#9488;å?@??{.&#9579;üç  í?@ß3ç&#9570;S.}&#9568;0  %.&#8319;?Oz&#949;*.å?&#9496;  ¬wdë???&#9472;.u&#9600;ñ
£0?¢&#9500;íYJ.1q±  ?Å?U?&#9618;è&#8804;      ;&#9564;&#9574;&#9578;&#9617;&#9617;??.ìv&#9516;  º&#9564;&#9556;@&#966;n&#9565;±.&#931;@t  Wí?.ó~º&#9562;.{&#9577;}
½nxÉ!í&#8359;&#8992;.·t&#920;  &#9567;&#9562;ä ?&#9554;ùî.ô-.  &#9576;I&#8745;x&#9492;H.&#9580;&#8976;&#9492;    &#8801;p5oëâi&#9612;.t?µ  »W?&#8729;»¿M&#8993;.?&#8992;?
½&#9508;ÜJå&#9492;¢¥.å??  }a¢¢xj_?.&#948;o?  &#9559;?jà>fö..Rqµ  P&#9532;&#9500;Ä&#9552;9&#9472;c.m?&#9570;  ]w&#9484;n&#966;&#9612;>?.g?h
1>î=>ohô.?&#966;w  &#9572;&#8992;&#9496;à&#8801;~_?.&#915;&#9600;±  &#9571;j&#9524;a£(g).&#920;·z  &#9616;p??&#9571;f&#9472;?.¿fb  &#9574;»WTO?0&#9565;.{&#9488;?
&#8992;²y)&_&#9561;&#8359;.&#9496;?&#9573;  â )&#915;?åq&#9516;.&#9574;&#960;4  ?^&#8993;&#9472;j?Äò.&#9500;&#9508;&#9508;  &#8804;pio?/b&#8805;..áê  ¬W ?UqYt.&#9570;&#9554;&#9558;
?3&#9562;ª2?`&#945;.&#9559;&#9616;?  &#9575;?&#9574;a&#915;d&#9617;æ.8¡&#966;  &#9496;&#9560;j|ä&#937;i?.¥?2  ?P?&#8730;&#9555;~_l.&#9570;??  W&#966;&#9555;½j?&#9574;&#9573;.?&#966;è
&#8993;3&#9570;f&#9575;&#9496;b(.&#8729;d&#9608;   &#8776;á*+ï&#8805;&#8319;.&#9576;?x  j&#9524;?êüß0*.?·y  ?&#9573;{&#9555;p?s&#9572;.é&#9524;?  &#9563;&#9616;x&#9563;â&°&#9516;.?K¼
±3ö?????.?a?  "&#9500;?å**&#9632;í.8½R  _?jf]/&#9618;M.&#8729;}&#9619;  !&#9472;&#9632;Pz¬?&#8745;      xëº&#9617;fÿò&#9571;.??&#9562;
4?I???â?.C&#8993;C  ?/?b@²z&#9569;.BU¬  jx?*u &#8801;¼.&#8359;3e  q/&#9568;8fm&#8804;&#8745;.y&#8776;?  &#8805;&&#9608;xf&#8776;ó^.???
4??&#9579;t&#8730;à?.q&#9557;$  ?»&#9492;b&#9570;*æ&#9532;.?&#9516;&#8992;  &#8805;&#8734;k7YDa;.¢&#9604;&#9616;  &#9496;qc÷&#9552;&#9472;&#9552;?.?!&#9492;  xt²&#9571;?ó»&#9566;.à`é
56ÿä??±&#8804;.?&#9508;&#9552;  -b*,a^&#960;ú. ?&#9524;  µK¢ì&#9632;ö?&#948;.ñ|Ñ  #Q&#9558;é`9=&#920;.M.Ä  &#8805;(£x?ù?;.&#920;&#9572;&#9608;
6_1?yg$û.æz&#8734;  b#&#9552;&#9567;?&#9524;u&#9612;.8_ä  ??:??£k?.ñ:{  q&#9567;ì&#9580;r>è&#9573;.ö??  ¬&#8734;ÿ4w&#945;b?.¬&#8730;y
?6#&#9524;&#9524;?&#9484;|.` x  &#9496;c5å??ü&#8801;.?&#9563;?  K?Qô·&#8976;?j.»??  &#8993;?qköùg¬.&#937;+v  y¬8áäì<?.??&#8729;
7km&#9573;vkfü.x/&#931;  çd?;k?&#945;?.&#9559;?Z  &#8776;?L?épƒ&#8745;.!&#9560;&#9524;  Q?&#9488;ÿ&#8729;Ö&#937;&#8993;.?k¼  y&#9600;&#9575;g&#945;&#9516;·(.#Wx
:?"?7&#920;?&#9608;.&#9568;6"  &#9564;c)eÿIj&#9484;.k?¼  ?&#9562;\%¬l&#9488;&#9492;.h&#9565;¢  [&#9566;&#9564;Q&#920;&#9574;ÿ&#9600;.&#9488;ò9  ÿi&#9552;'&#960;c¢>.y&#9492;ª
7#=&#934;&#9566;µ#&#8734;.y*&#9580;  ??&#9496; c?&#9566;&#9556;.&#9565;º&#9573;  lh&#966;é4$r].&#8734;ô¢  Q&#920;¬zST?$.?Ç&#9492;  y¢u?vé&#9563;ï.&#9618;&#9569;`
8=a &#9568;ä&i.&#937;&#9508;?  cö*\L??&#9632;.&#9559;C0  l&#9524;ló?jhh.&#9552;&#9508;#  ¢rg!T(&ï.$&#9516;?  Yxå/5?&#9618;&#966;.&#948;&#9560;&#9617;
&#9568;8??é&#9492;é?.&#9574;ò?  &#9568;°*&#9568;?@d?.?&#9617;)  L(&#8359;&#8804;ºDc?.&#8804;&#9600;&#8319;  «r?k¼·û&#931;.&#8976;#ú  &#9474;?zµ&#9496;ôºy.?V&#9472;
8??&#9600;Q8H?.??&#8993;  $&#9561;&#8804;:±&#8801;D?.?b&#9484;  M&#9508;8&#8730;~&#931;¿&#8729;.?]&  ¬?&#9571;R±?&#9619;:.?û?  &#945;gp&#960;ô???.?&#9564;&#9579;
?°&#9564;]&#9559;8?&#963;.&#9619;&#8730;&#9555;  d?&#9474;g&#9559;&#9608;&#9553;k.&#9575;_&#9496;  [mª&#9573;?ü&#9573;p.écu  Ru?K-p!&#934;.6    &#945;?%Q&#9559;îGM.(&#915;&#9572;
&#9558;?9-"q¢ª.&#9562;&#9604;A  ??dRh&#8804;&#9570;R./jy  m,&#8359;p&#937;^z&#915;.&#937;lt  ]R&#8976;Zè¢&#9500;?.ñ`&#9617;  '&#9579;?&#945;xd&#8993;<.xHD
&#9472;á0?? &#9559;&#9616;./    ë??0h?&#9617;y.?ªR  &#9553;M±ú&#9553;Ä&#964;'.&#9524;k£  r&#960;^ô&#9496;t&#9604;&#963;.&#963;dî  ???<??&#9564;&#945;.ÿ&#9616;&#8801;
&?A1&#9558;ó?x.&#9608;?c  &#9557;&#8992;&#9484;é1&#9556;e?.:·d  MYHCX&#9564;3?.?ƒ?  S&#9573;4°2ƒo].2så  &#915;?&#9619;?.0??.&#9580;5&#9508;
&#8730;à?&#9492;?9?x.&#9553;&#9524;&#8745;  &#9555;&#8319;?&#9618;????.ë2?  mµ?*÷k|ó.&#9632;*Ñ  &#9524;??Sâ&#9618;?«.L!?  &#915;?n8&#8729;?jq.e?f
°±{¿?#ÅÄ.Åäv  :?ë9W"J_.SMZ  ñ0Pp?ê&#8729;&#9472;.&#920;ñ&#9484;  s&#9500;&#9616;åoù¥(.&#8359;&#9617;g  ~&#915;o??h±÷.&#8319;E÷
&#9472;&#9579;?àæê(o.{·W  ]é&#9600;&#9567;&#9557;Å`é.l(&#9564;  ?&#9580;_&#9604;&#9570;ñ?e.^âa  såpÿ(9&#9552;}.&#8992;ªa  &#915;qhaw=å^.&#9575;&#9564;Ç
?â?æ&#915;@<&#964;.Q?a  ê?=BaD&#9571;T.µ?ñ  ÑO_&#9554;û+y&#8729;.?üO  '¡&#9563;Sé-&#8992;&#966;.&#9560;ªç  &#9572;&#948;&#9555;$.?&#9617;p
ååì.&#8805;v&#9573;       ±ë&#8976;î&#9574; ú-.g&#9569;s  &#9556;:&#9472;N??@ÿ.â3ó  Sñ:&#9577;&#9564;&#931;w&#8730;.&#9500;3µ  &#949;&#8993;;pôiæ?."?u
&#9617; ábs&#9572;?G.D1è  ?eºa?&#9552;?ü.$ëJ  ñY&#9516;&#9516;Ej?&. (/  ß£???1&#9563;&#9571;.?çé  &#9579;&#920;°á&#920;½2&#9552;.pt?
ä¿ç&#9561;¼c??.?&#9571;&#9577;   ?~ê£ßAç.?Å?  (°~>ñ&#963;ß?.&#9563;X=  ß&#931;ë??&#948;â?.7÷{  =&#920;k&#9488;_OC).ê?[
&#9566;{ªcç&#9579;?&#963;.&#960;-9  <ÉÜ`î?Æd.&#945;o?  n&#8359;&#937;¡¢qs&#937;.&#966;v&#9576;  T&#915;?çCNT@.&#9570;¡?  &#920;&#8993;t?*ô÷7.%&#9632;{
å]&#9558;?? Çö.?&#8801;&#9575;  F&#9604;&#9558;5&#9564;2!ì.g&#9488;}  Ö£?äÅm&#931;?.$??  ?? t&#963;&#9573;&#9524;?.??&#9616;  &#960;&#9552;ó"&#9579;&#9561;µé.&#9574;?&#8805;
¡àcpo?&#9562;?.ä&#9618;,  FçFA?&#8804;q.&#9579;&#9565;&#8776;   o<Æ&#9574;I?Öl.co8  u0_os&#9612;?z.m0ú  &#963;(?$6;ó&#920;._ÜÅ
âÇ? &#9552;&#945;Éb.z-#  f¥Kè??&#9560;Ç.&#8729;?$  öÆûê0 ?ä.opê  &#9577;ù6`&#9580;y&#934;&#9619;.&#9516;&#9604;ü  &#963;:f&#9556;&#963;&#9618;&#9632;=.?&#9604;&#945;
ä&#9578;ç°&#948;&#9563;&#8993;&#9564;.&#964;^s  *&#8805;F?M&#9600;ù½.&#949;g-  oæ«&#9516;?&#8801;&#937;ñ.,&#9554;?  &#8776;Ü&#9608;Çª?üç.2&#8776;d  &#963;&#9573;@?o?&#9516;á.&#8319;vq
&#8359;&#8805;æ±&#9612;)^?.j&?  F&#9559;]ó&#9575;**°.?1   óå&#9484;&#9496;yP«D.k&#8359;}  `ù:&#9576;&#9562;?k%.?{&#9604;  &#931;R?A?|>è.j&#9532;j
&#9555;Æ&#9618;q&#945;¿?v.[.&#9571;  Fq?3g&#9561;?&#9492;.&#9572;¬&#934;  ób&#915;&#9558;&#9572;?a&#9572;.&#9579;?é  &#9566;?&#9488;ul&#9571;o&#9559;.¼&#8993;%  &#9578;&#9575;?&#963;&#9600;tà&#945;.ñ&#9576;~
a&#9566;&#9580;?éßü1.6Æ&#9564;  @gÿéæ&#9580;p&#945;.ù&#9569;1  ö-&#9573;d`&#9492;¿g.»rú  ?ùr&#9557;&#966;&#9557;n?.??u  }&#963;?U[&#9532;A?.&#8805;&#8976;"
æ? tò&#948;âé.ç??  g&#8804;Y?t&#8745;]x.÷&#9568;é  ö&#9532;es&#9616;?&#915;?.&#9576;âò  ü'?¥`?ß±.?&#8801;&#937;  {&#963;x&#9557;????.3»?
&#9570;&#8776;æùù&#9619;:ƒ.P&#9552;&#8319;  &#9557;h&#8992;ª&#9562;&#9579;c3.Üb&#9571;  ö&#8801;H?(¿{.?&#9632;&#9560;   u&#9558;?û!&#8805;?ê.?&#9554;6  &#9562;&#964;ë?&#9557;?ïû.&#9580;?&#9553;
ª«@¢K~&#9562;?.&#9532;HI  &#9557;hë;*&#9559;äá.w&#9577;?  ò?&#9492;&#9554;M?F&#964;.&#9558;    u?u?îísg.?&#949;#  ¬&#8745;&#964;O°K&#8745;&#8976;.?&#9568;?
ä»lìi&#9579;ë?. X&#9488;  ??hüÜå?!.???  O&#9563;·Ö&#9557;Å&#9570;J.y»ï  û?ÿ&#8805;K&#9563;&#9554;?.&#9532;k'  &#9554;°&#9604;&#964;¬y&#8319;<.tî,
&#8805;Å&#9474;&#9578;ñ?*¿.úü&#9492;  H`&#964;±ëY>?.ég&#8359;  ƒ&#8993;ºô?j&#8359;\.]&#966;&#9612;  &#8993;??ùz&#8805;^&#9578;.é&#9474;¢  ¬?&#966;?ó0öü.&#9576;(?
áö?u&#9556;&#9560;î&#9565;.?&#8805;o  ??@'i&#9579;â.??&#8730;   º?&#9576;ó&#8976;:&#9496;).ym&#8804;  &#8976;?&#8729;&#9496;v&#8805;3v.??&#9555;  &#937;?½&#9567;yd?&#9574;.&#9565;ç&#915;
&#9604;ào&#8734;&#9562;&#9564;?*.QrA  ?ï-?áº«?.~ú&#8805;  !Ö°?Pc&#9556;â.ä&#9619;&#8745;  Vñ·&#9557;&#9570;?Åµ.|é&#9524;  ?'&#9565;&#937;H&#9560;(I.å?ÿ
Å«&#9566;?Q'PÉ.`zP  ?¥îç&#960;'&#9612;%.&#8319;&#948;?  opvk&#9516;&#9573;?&#9618;.3°&#8729;  v&#9577;&#9553;'*&#9555;&ñ.ºôi  *&#9577;&#8992;2kp??.?&#8976;8
&#8801;?A&#8801;T&#8734;60.?)&#9571;  îe&#9524;?&#9516;ví&#9569;.?D&#9577;  ÖwW&#9552;ÑQ·?.«&#948;w  V&#920;<<!?U+.&#9579;~C
oldrocker99@oldrocker99-desktop:/media/FFF4-D0EB$ 

Am I completely hosed here? fsck wouldn't do anythign either, besides offering a switch it refused to use.

As I said, May Day!

:guitar:

---

### Post by Cybie257 on 2009-10-23
You said it read perfectly fine in 8.10. What version are you using now? As I don't think that 'should' make any difference, you might want to try booting a LiveCD version of 8.10 and see if that allows you access. 

That's my first thought after reading your post. 

-Cybie

---

### Post by niteshifter on 2009-10-23
Hi,

First off don't write anything to the drive!

Post the output of:
```
sudo fdisk -l
```
That's a lower case L, not the numeral 1.
and:
```
mount
```

Next thing: If the above fdisk command's output makes sense to you - if you can identify the problem drive's device names then post the output of the commands below.

Assuming the problem drive is /dev/sdb with 2 partions /dev/sdb1 and /dev/sdb2. These are example commands:
```
sudo file -s /dev/sdb1
sudo file -s /dev/sdb2

```
Do this for each partition on the problem drive. What "file -s" does is tell what file system is on the partition. It doesn't write anything, just reads.

---

### Post by oldrocker99 on 2009-10-23
OK, here's what I got:

sudo fdisk -l
[sudo] password for oldrocker99: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1043a06e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097505

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706    b  W95 FAT32

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17fa3c38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       24791   199133676    7  HPFS/NTFS
/dev/sdd3           24792       24792        8032+   f  W95 Ext'd (LBA)

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b38ca


oldrocker99@oldrocker99-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oldrocker99/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oldrocker99)
/dev/sdf1 on /media/FFF4-D0EB type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

oldrocker99@oldrocker99-desktop:~$ sudo file -s /dev/sdf
/dev/sdf: x86 boot sector; partition 1: ID=0xc, active, starthead 1, startsector 63, 1953520002 sectors, code offset 0x31
oldrocker99@oldrocker99-desktop:~$ sudo file -s /dev/sdf1
/dev/sdf1: x86 boot sector, mkdosfs boot message display, code offset 0x58, OEM-ID " mkdosfs", sectors/cluster 32, Media descriptor 0xf8, heads 255, sectors 1953520002 (volumes > 32 MB) , FAT (32 bit), sectors/FAT 476701, serial number 0xfff4d0eb, label: "           "


So it's not ext3, but FAT32???

Now what?

...and thanks for the replies!

---

### Post by Cybie257 on 2009-10-23
> **tribirbu said:**
> looks good and congrats. hope you enjoy the car like many of us

HUH? :confused:

---

### Post by Cybie257 on 2009-10-23
> **oldrocker99 said:**
> OK, here's what I got:

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oldrocker99/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oldrocker99)
/dev/sdf1 on /media/FFF4-D0EB type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

oldrocker99@oldrocker99-desktop:~$ sudo file -s /dev/sdf
/dev/sdf: x86 boot sector; partition 1: ID=0xc, active, starthead 1, startsector 63, 1953520002 sectors, code offset 0x31
oldrocker99@oldrocker99-desktop:~$ sudo file -s /dev/sdf1
/dev/sdf1: x86 boot sector, mkdosfs boot message display, code offset 0x58, OEM-ID " mkdosfs", sectors/cluster 32, Media descriptor 0xf8, heads 255, sectors 1953520002 (volumes > 32 MB) , FAT (32 bit), sectors/FAT 476701, serial number 0xfff4d0eb, label: "           "


So it's not ext3, but FAT32???

Now what?

...and thanks for the replies!

Just out of curiousity, do you have ntfsprogs installed? check Synaptics and see if it is. If not, install it and see if that helps. No reboot is needed, but you might want to unplug the drive nad plug it back it. I'm looking at your post for something else but this is a first thought from what I see.

-Cybie

---

### Post by Cybie257 on 2009-10-23
Overlooking this more, it seems like the drive is being mounted as a FAT32, when it should be mounted as an NTFS. I doubt you would've formatted it with FAT32 due to the large size of the drive and the limitations of FAT32. So, definitely check if you have NTFS installed. Do you have a windows computer that you can connect it to and test? If it works there, then it's an NTFS partition, most likely. 

Report back on any attempts or if you have the ntfsprogs installed and I'll see what else we can look into. 

-Cybie

---

### Post by oldrocker99 on 2009-10-23
ntfsfix (after I installed it) said that the volume was corrupt, and that I shoud run chkdisk, which I don't have (of course). Running fsck gave this:

oldrocker99@oldrocker99-desktop:~$ sudo fsck /dev/sdf
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


oldrocker99@oldrocker99-desktop:~$ sudo e2fsck -b 8193 /dev/sdf
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Kind of recursive, isn't it? Should I try another -b figure? 4097? 16385?

I REALLY don't want to lose this data. Booting from a Live CD gave the same result, as did unplugging and plugging in the drive.

Not quite at my wits' end here, but it's getting there.

:guitar:

---

### Post by Cybie257 on 2009-10-23
Well, if it's an NTFS formatted drive, then fsck probably won't work. But, I would find a friend with a Windows computer and plug it in and see what happens. As you saw, it was saying not a valid ext2 partition, which it isn't. 

-Cybie

PS. Check your private msg's for an email from me.

---

