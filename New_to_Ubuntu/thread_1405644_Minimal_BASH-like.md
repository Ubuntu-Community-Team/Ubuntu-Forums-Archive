---
title: "Minimal BASH-like"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by shadowlands on 2010-02-12
not sure how to post this.  I just can not get the system to boot. After it tries I get the following message:[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completion.]

Sh: grub>


How do I correct this so I can boot up my system?  Thanksin advance for the much needed help!!:KS:popcorn:

---

### Post by yeats on 2010-02-13
You will probably benefit from this... I'm assuming you're using Karmic (GRUB 2)... previous versions will be GRUB 1:

[http://grub.enbug.org/Manual#GrubShell](http://grub.enbug.org/Manual#GrubShell)

---

### Post by shadowlands on 2010-02-13
I will read it and try it.  I am dual booting with windows XP.  I can get in to XP but I can not get in to Ubuntu.  boot up > **chrissharp123 said:**
> You will probably benefit from this... I'm assuming you're using Karmic (GRUB 2)... previous versions will be GRUB 1:

[http://grub.enbug.org/Manual#GrubShell](http://grub.enbug.org/Manual#GrubShell)

---

### Post by luckydeveloper on 2010-02-13
> **chrissharp123 said:**
> You will probably benefit from this... I'm assuming you're using Karmic (GRUB 2)... previous versions will be GRUB 1:

[http://grub.enbug.org/Manual#GrubShell](http://grub.enbug.org/Manual#GrubShell)

if you are talking about ubuntu 9.10, you can 

Press  and Hold down Shift during your system boot. You will enter Grub menu then. If you can see your operating systems in that menu, choose one and press enter. 

Hope it helps

---

### Post by shadowlands on 2010-02-13
Yes, I am using karmic and this started after it was updated.  last night.  I see the choices and if I select XP  it loads up no problem.  

My problem is getting the Ubuntu to load up to the log in screen.  

I tried to follow the direction in the link and it looks like the problem that happened a while back and in order to correct it we used " linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=ubuntu/disk/root.disks/root.disk ro"


"initrd /boot/initrd.img-2.6.31-14-generic"

"boot"

That did not work.:confused:


so what are the numbers should I put in to get it to work.  That is if I am correct with my line of thinking.

Can someone please help me out????

---

### Post by shadowlands on 2010-02-13
How do I load the kernel.  I typed boot and the message displayed on the computer was kernel not loaded.  I am using wubi and it is XP.

Can some one please help me. I looked back at the archive and i followed the directions and I still can not boot in to ubuntu.  Help please!!!:KS:popcorn:

---

### Post by meierfra. on 2010-02-13
> I am using wubi 

Have a look at this how-to:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by shadowlands on 2010-02-13
What did you use to open the file because I do not think this will correct the problem: f1íém                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       UªëfHdrS                                 ÿÿÿÿ                ÿÿ   “  ÿÿ   “                  € ÿÿ    .‹` .f‹. è  [ëv ÁëŒÈØPh‡ Ëƒè ŽØ‹ñÁá1öŽÖ¼ `üŒÈŽØ¸ ŽÀ‰÷óf¥ê®  f‡îf	öu	ŒÞfÁæfîf¹   fÎf¿ ‚  èI 6f>\‚°*tf‹6 f‹ f¿ €  ë
6f‹‚fÁL  è f¾Æ6f£‚f¾b 6f£‚¶ÿê   fA€áþRfVfWfQfù @  vf¹ @  fQf‰ð‰6B fÁè¢D ˆ&G f‰ø‰>J fÁè¢L ˆ&O ¾0 ´‡ÑéÍfXfYf_f^s¾ë
fÆfÇf)Áu¢ZÃ´1Û¬Í< uùëþmove memory fails                                                                                                RV¾è9^¿ôf‹-ƒ} „â €|ÿ tFf‹f‹Mf1À°9E‹E)EffƒU Ç ‰Df‰\f‰LÇD pPÇD  ´BÍ‚¯ » pëff‹Ef	À…— f‹f1Òf÷4ˆT
f1Òf÷tˆT‰D;D}y‹*D
9E‹E)EffƒU ŠT
ÀâŠL
þÁÑŠlZRŠtP» pŽÃ1Û´ÍrFŒÃŽE
XÁàE
`Áà‰Á1ÿ1öŽÛüó¥¾#èW aƒ} …$ÿƒïéÿ¾%èB Zê ‚  ¾(è6 ë¾-è. ¾2è( ëþloading . 
 Geom Read  Error » ´ÍFŠ< uòÃ                                                                                                                                                                                   ›  êÈ‚    >™ y  . ÿÿÿÿÿÿÿÿ/boot/grub                                                      °*   þOQä\            | ‹S¹L  
 ¾   ¿ €  üó¤¸ž‚  ÿà‰ÐÁè1Û€üÿtˆã‰‚  <ÿtˆÃ‰‚  Áê¶ÿèð   ú1ÀŽØŽÐŽÀf½ð  f‰ìûgˆ8ƒ  Ífè„   @è  ¿   ¾Lˆ  WV‹
‚  
‚  éL  QèŠ  Y_^+
‚  ó¤¿û  ¹*p )ù1Àüóªè…
   v ðÿ         ÿÿ   šÏ ÿÿ   ’Ï ÿÿ   ž  ÿÿ   ’  ' @ƒ  ú1ÀŽØgfhƒ   ÀfƒÈ"ÀfêŽƒ   f¸ ŽØŽÀŽàŽèŽÐ‹$£ð  ¡<ƒ  ‰Ä‰Å¡ð  ‰$1ÀÃhƒ  ‰à£<ƒ  ‹$£ð  ¸ð  ‰Ä‰Åf¸  ŽØŽÀŽàŽèŽÐêìƒ    Àfƒàþ"Àfêþƒ    f1ÀŽØŽÀŽàŽèŽÐûfÃ‰Âè‚   8ÂuÃUè˜ÿÿÿ¸ $„Òt@Ífè>ÿÿÿ]èa   8ÂuÃä’$ü„Òtæ’„Òt	èG   8ÂuÃäd$uúäd$tä`ëöÃèêÿÿÿ°Ñædäd$uú°Ý„Òtæ`èÑÿÿÿ°ÿædèÈÿÿÿè   8Âu„Ã¹d   è   8ÂtâõÃSQ1À» €  SŠÃ   Š[ˆÅþÍˆ+æ€æ€SÃ   Š+(è4[ˆY[ÃÃƒ‰Á‹‹UôÁê÷â;Eðv(‰Eôº   +Áêøœ}ô   sÁeð¬ˆEðÁeôÃ)Eô)Eð‹Áê)ùëØ¶É1ÒRBRPQRÐè¢ÿÿÿZYs	‹D$	D$ùÒXÑ$$âáY)ÊYÃPƒÀ èÿÿÿXrj ±ƒÀ‹T$ÓâÐè´ÿÿÿXÂÃPƒÀè[ÿÿÿXrj±‚   ëØj  ±ëÕˆEøªÿEüÃU‰åƒì$Wü‰ß¹6  ¸   ó«_1À‰Eü‰Eø‰Eì@‰Eè‰Eä‰Eà‰EÜ÷Ø‰Eô@±Áà¬âú‰Eð‹Eü;Er‰ì]ÃƒàP‹UìÁâÐPèÜþÿÿ‚š   ‹Eüƒà Áà‹UøÁêÐº   ÷â6  PB‹Eè÷Øÿ4€}ìr/ú   s@1ÀÐ$$ÀPRÁà„   D$è…þÿÿ’ÀZÒY8ÈtÑú   sR‰ÐD$èfþÿÿZÒëçƒÄˆÐèÿÿÿŠEì<s0Àë,<r,ˆEìéBÿÿÿ‹EìÀ   è/þÿÿƒš   ‹EìÌ   èþÿÿr8‹$ð   è
þÿÿr_€}ìÆEì	r€Eì¹   ‹Uè÷ÚŠè©þÿÿâöXXéèþÿÿ‹EìØ   èÕýÿÿ‹Uäs‹Eìä   èÃýÿÿ‹Uàs‹Uà‡UÜÿuäEà‡Uè‰Uä¸4  èþÿÿ€}ìÆEìr€Eìé®   ‹Eè‡Eä‡Eà‰EÜ€}ìÆEìr€Eì¸2  èãýÿÿR¸   9Âv‰Â±Óâ‚°  èœýÿÿ‰Uèƒúrc‰ÑÑéI¶Â$Óà‰Eèƒús‹Eè¯  )Ðë9€é1ÒÑmôÑâ‹Eô9Eðr)Eð€Ê=   sÁeôÁeð¬ˆEðâØ±ÓâUè¸"  è4ýÿÿMèÿEèZƒÂ‰Ñéßþÿÿ                                                                         z:[DùòVÿWj5×wKþk;Ybð,×Y?ëa)<¤#¸8*&+™¶<±~UŒ2’Ú‹Õf^õ*°[áæÃz&(¥çsK°·„È[´ +Õ¼xÅ¤ *Ïp|ËmÃêÒ&b‡ØrošG9 ú¢ð²dúbÕ"’®êa£GBŠÖtJà‚«COZ»œÉ=”Dœ¯6NJ7MÃƒØ^Ò%Ó³Ý¿(Ì46±¢”uÊ4»ÂÙÐ{¿<‚–™úÎ¬Ì°ýÃwpY+eÁ»ûÃ{¿Øý?3½§
÷Ï
j~B#¾‚Têñœ—¯9åIÈBÄz>8.Þu—n„ÃöV¨îÏQ@*KSI²žÆâæDÛY-°Ê† Ï®ÀWÃ‹Ö¿/¥9ÁÕþñ§†þáÉÍçM|•OG|\âàÞ…ÄÌâÄç1øW]¬pªøè€eJƒêz	W“¬|hÈ¹®
ÈL*tz@££Ð‰]oì6l:æ:ºë}\Ý‘6æÈÁ®›¬ÌVC=Øš]ÙØdCe¡¿ÙÊ¶Ž!R—¤¤·=î¡ûÜåþ‡×<˜KÑ#È}nª£?ø$Ã÷cêV•ÙD¶avu	@v\¼X¶bƒ÷T÷Ã»Ó+¶!ÄEdJ†òRÿƒ¿Š|\rÔ_v³"%m‘Í"Šð›#’‡´ûû¬\8bÙVaÏ‹`%hASs×‹ê?qOß,ÅŽJûZ;ãz‡pÐ^8‘«„ÝH»‚C-³,úx† Ñ×1ù*-ÂîR!z%î£KÅ‡JqÊ=Ð"Aè	ÊŒb{êó®¸…
Ý•¸.×ÄÁ Dâ™8€kþ*-”1I¹*=•¥÷‘kqr{Ýƒl27`ÂÛ“î#TÖZ¡1ÿ¸øP*{ÒœùÐ;ìêT€Ê¯¿ŸDÚïÏâŸáîÛˆepúƒX«AÛ5ÆrXö
53Žª¼¹¯h¥þ•NÐÅNó2%/5@Qp¦ãT²Àwº§#8ÀîA2:|üþLÒ*\ú²X-¶…²Ø™0ä™.cj©žIs~ð”:Co±g.CºF•‚ggÀ¥°412§Ë4ÐñŸQ‘êÂr‹Ó©kMômv$Ø÷»YƒêØ[˜MbØco×ºƒ3¸6ÅÛæ…c?+Â€)XÙ›tQ°î^©ÊØhôìÔÚÙ-Šz,q¦ *Áü¬=i‡ùú©ô+ØÆj9þä*³½yø†-q1	AÊB»Æ4óFø^Î¦jß*¶\'˜¬,6ù*3xï“Â(îÀ&6èý†·ÞÁŽöõh*ø›T7c¹FFë)N
SE,	–F°*nC²…¿Ë´òý	ù_8Îä2Ûò3*mw=&è*91=>ØWR^M†Y‚e—È:2+]ùc¡R¿;þÕ?3áóÓhZyÌÕ»ÈËs«HôFyjî–Ù!l™®üüD_ëÎÇ¦4½^vH–Ð:ÅÁd•ÕýæôÐÌfwA§*uÕLC¨÷Z1at„“pboU¾-iÅì7\‚!p‚êRç´ùßÃÙ(q.„¹Æ ñN™4 ¤ÁPƒ[*Î4ÊUKt*öà>´Ý¼4þ‹fÿÝz\¾éŸûŒ)Ÿm4ß`êE¡‡€ Œ'Ùmåhq:åæf˜tm•{hïÀãZm&zDÓIÐˆõcŒÅ‰ä5VÔž
uš…ÚU<Vj&³ÙÃY”Òˆv”½™fkmµ0‰76À‡Œ^æÇäšÛ6Oô¬Oà™%—‘Ÿþ.j/
—&ä¬ƒUž%ûïØMÄ‘QÅ™k˜Žg¼™{-—‹Ù«ýúQO…ÙÐ3QUà0’oV/Øþ÷î»bL¨€I êÈ?ÞµÖ›Ô(ÒãˆƒÝÎÄÊ(Li¦LZêØi3[‚c±Ï¿îMW	ÐxÎ9²ç‘6îºÃÊ*?‰•«ÞŠN”÷¹Ü)ò±³â2k€«™d"3Æ=ÆI›ƒÅ_Ã¡ÃŠ	ê#˜òær¢-‹¶*t°yßù/”Ú‰ %–	Ÿ¢]«ïðÿ’pªKJ`ž/¥n¨3¾Ûò}CKMËG]
ŒUK
z7ø6í'ÖÙ{#:€ÅÕ¨È
P¢‡/¯ëFUƒ…–é_ÏÙ‰Ló¾¯O÷T:	ÃµÉÏ27‚õDøÆµ„cÕegô<ÍÖ!s%æ™~°”ˆnX	>@’:øíåÈ¯FÖzž-~²ã~;µH¼÷ó„`‡ÊwÑ4'2©Í[‡Æ÷ï0
,U°ÿÑ	7´³º¼6^Àtf¼kÞÈ0û2|M^ ›ïÄ<Æ£fyˆ	%Yµoè‚Hœ†ß¶ò³bœég8]ì7 ö’ËNå¶¸uËaãN¢vÎf|¦¢5GBMVé®&f‡1Â%då%7ûû2Ÿ1éÍ_
PÅ¿W<Ô<²ÚºsÝŠŒ½ªºáêñ˜4á…´‰?VBQÝ=èzžyu‡QÀØUê•*Äó„»ÊtCÆüe*yt¥ûwcÕdÙA£¬Õ']üeo{D`ž÷h²™Æ‡Ï—ã¢Û„	ÚŠa”ÈÊœ§Ùa¨S*EÓio=øÁIŽ‚;Ÿ¤R…f˜²3A5ó}(\69Ê9mŽµöûìÂÿÓy)ípúû!'yÿ±iˆÝ7sl4"ýYƒ…¤è;û¨O¢ùn)·ÅXÐ3*§D^k’º¶‰âb0(å`@uô"|ë
ïë»QÏ§eÍ½ý¤†Bni½7Å},+æ’?ÔÐ³m„–²ï`5pÅ!î¹è–ÎXÍ¸lô2c|6Ûñ¸°ý˜*çêâ×º×Œí;&¶FÁ›”»c‚'dãéÛ±²XJðºhÚ÷rù²*/O>M• zZšÄ¯¾ax~ªFø)úŽsÎóAßõNÜZ…í
$hÓ¶±¾¼l2±F¼V$4al¶?3÷!U©kKS;
»@‹‡9?âaÕ?Èî6±KAôÑCÐmg!¾’[¤Íh +èèUGqXÑìÔ®-õýý«¢Ö¥Êá¾{¯ôp—>#Ø§|äýÛCŒY84z»sL”§ŽDSli‡D/çJ%It]æw
ÁïT®%3á|©Ó‘I4#w%ÎOQÀnFŽeé$%¦¶•ÛÚu>ýLÕ8œ#l‚t~¢Ïn`0Õi[Ã¥J}×¨‡¿Ý™ž±û“2óYÊ!YæIGl(OñåD
2Â?\
ì,JõlBvHa'Þ¤pvï—)ûeu~²7^¸Ü,1q*ôÕ×E±‚G0Y‚l…õ€<À%=ôÅÛ³‡ÈÏB_cá*Vzx˜ºUÎÌó÷hñÿ&ò_~–Œçû +ô]¨¢·ão%tÒ…–iñð+âÿÖkiøTÛæò¡{ŒPå¨Íˆ"¶@Q–¨µõ…Òþ
k}d»á1|§0þa´8Wh¨g>Ä¨áÌ7Ê‰°;ˆ:¦Ýë²r‰º¯Ã€®Ã÷,nÚI :dÿdå+Þð@¢qQâŽ~ºdâªn5t~bL¦_2·¹:jÕ;±O—q.àwÊ:ªº:ÿi„ˆ*y¥£ò*ÉL£Z,ƒ
kÚË'R/4ä¸àÏR¹W¦, `;-$5ŸžÓktº÷Ì¶¨Q>¦¤Å×‘ÛÅÌç÷áJ”È{B*=nÜv¾*—#%ÆÞ†JI‘nmãíz”£oÄT8“î‚:ØVj[sDG dŒjÔÖB,=ËU’îü¡8yoÍv®®HŸBÉCšu+¼xŸÆ@ TýÛöx¥‡V.¦œî¡ðÚD7ÍDÓ*qu¹ØÏ#&,CÃKUË©Õ$*Lkã%êë®=ìŸ°YÂ†FÕ‹‡t¾'•«'¹¯ž_+
ê7H§ etäw#,ñÐEÜ?iÌUEØb~´ž´„EÓØdf˜•Y<KƒÊBË/MmÞm1s µoÿ‚x‹Å¸6…y“V›f‚ª³æævxóéŒí1—ô²È†Qä<P$š°‡™MÈ	¬áK® y…XQ‡°‚Ù7™†»Ð*ëpCæˆ°i¼ß"ËA©mi.
ëQ~gY¾)Ÿ¦{öµa-å/Ž»ï[ñ§`!ØÏ_9ð¼)×*„Š)Eõ‘w(Ž*›–îÄ‰ÊüZý`pNø¾k%<‘‡drYÖ
KŸ–Ëé¨*WŽçÐÌÒ,0Ý\…R!èÌS=*î¨kØåÙcñ×î×Äzvyøn‡MÕþ?®ÈÁh:ù]ÿ<Ý»)—*ˆ :‡¨~Ÿ¨’h*EÙÁÕT”¡¤¿+™ð"çSvw;5ãýÇ¿dA<¨ìä¯Õ®JÉð{´è)íI¬ÅYM|L”n_`Ï8”zÕòäÓ¤ÂéþÕgä—Äôã¸+—ÜÌ(à½ÁkP\p¹uÉÜE5føÀAÖ‚S
cB€ª*š%3Õ›¿Ck~_å?§Mä„õmæá‡ÄAãR†Þ¤4dzìá{øÅÁK°ðí©ØV³Ô˜)X¨ªf[é©áPÂÙ¯‘€tX8Ü·g¸$o<‘ø˜Z3GWvË˜Ü2a¥Ï—÷«g£&ä¬B|j`oÂ^`Y6@¦Q¾¶»À²ÍÂ‹û“êëâ¾Œe¹iV!„ÀË–‚t‹ÝfŸÙ1¶}˜Ëçå|”-=÷Ì0¬‹oõtV…ÀÀú[,1?é²¶Å¯fb]dI gÖÝ–hÓÀAšYKÖâ pL·ýN*Ž¥˜TúM…¶¥$¢h„!×¢…ü˜‰äÏ·<Éë³#ö}	\@^‹»"+û:Á ä´ê?ˆU¨£½ºÇÛ®
çß <’¹¯ßÏŸ *g9m;jÈJÉZ[$?l1Ê¬naz é˜‰ÌFà¢zc2Ë”X>f}g*¡’ú†	ÇK[Z3
Ç7ÄokTÝž‚Ze…M®®úOÖJ¨É :FÒ|Šý•_—ô‘ûLùQDûAÃÊIŽHÖÂ®¤ä-_`jn<_))ä°û›®ÛµzøeAƒÉ6ŠlS_ÞfON¾*	`å'6‡|@×*˜;ØLcM2µ–ˆñCRÕõÙ6Ôÿ‚Á4¼Ç•‚§Î.Š°‰ó(Hî÷ÇÜB"ðwÜ”uÑv×8HžÇV[®cF[Þ¤Ñ\*”Dßkrëá1Ìíýf½¥æ;ÏËÏö:ÌzYKi
©ÎÊ™0˜×WßŸ\Êh¶1^Ú;gò„cþè;ôØ•6?qNº¤ð–²Îê>ÇñD–ªd\t‡zH— †þ7ZÉQ§ÍEÚè÷R^!GNËßs¶
‚{/({Ì¹GÙ‹qIË	§ú2¥îbÆqb0½hi*‘·“5ë,Gj2üí@
B;Hý¡óëT´‹å_xø0<ÍSñ®K˜ˆXÔâqùêñ½Í9©S…ëo¶´Ž.)ºFGa9âHõoØGÑr½çå·x”žÅ9q)²@pYa«ÜtOïJ¡-Ò–ó>™™y["TžyWD_ºùK×û_^¿àG„.»0KðMWyú¡¡ÕÐÛ»)¶QÓ£ºïxàÙžuÌçB¿B”Ã“ •h¸=Å‚þ7‹>´ÀPpñŽÈäyŽ¹1ô"|¬ŒaÄs'©5ÒGÜó¶wÑ»7{8ËæY¾5jkôõG¯;q¹wzü±ï‰8Í—%Ï&ëíZµòp õ˜æ¹?˜«ÈYºšp(êØT³Ó5S^»¥mæ
°Žü|êÉ!'ŸŒü%a*Ý;ˆPÝÐ`À©1°?rÓåW¥wKÅaŒs*6‹´W§„TqßM)ö»“*ÈÙµÌ+=ßŒ¢@Vb¼_Á4{"”œÈûF‚¸„˜ÜåúÖŠ#°-ç€³¤Ò)ò8ÚøÒ^ÛlsoõÀj±¦÷°[úþÍ&û¡Ó»Çût‘hª=N W)Ó3zpµàã—û8¸
^‘WíVd‚ ²*UtúÊ\¨;àB_šž<Ü˜¨hA÷ªipB»üc73n;,hØìpcÁ63ƒQ0µˆráðêLÔLF€G
‚ýzØ1
;#®‡'³2NÜ*‘5„súÑ&Â:’©TÞ¢ñ>®m#A›aE¬±á
¡¹[Y´?ÓHS!ç-hŠYÂxøDqªÐ§«¬“±eh¾áF•¼I¸äïÜöÂÎ·AÀ&(Äÿ^êPRËhù)™wLOu3PlÕ‹Y>uë’“¼Fm‰aÙK]8¡
;=CÎdùTB>Än–ãÎÙvô÷åXô{å…‘7x\ñ/ÃühÉ„£ëO1(sêèYÄý2mË¢N¥ú+)Éñ5áÆþÎõeÛˆ†‰»ž÷ÀO`vþ]C|I/Ö(‘§Š¬k1µÌ1SÔµþGêBÍ÷}&/HS…–Ù~¥Xõ¯–ÑêH7d½ßrt…B6#ª®{›3"HXhN¸	]bêŽ³~VÝP|ho=–äý=?Ý™ê¶ùZ§ûdþ’Hí£¸³®VÝf§IÕ5ˆ(¤ï’–—Å¯æ<]Hè’¥Ýî¤žìpkTï@(+ü¥¥þâp¼EtÉ¡¾Ã§K–KÚk¡È–ž“+7ÁtQÃ…©ÎÚ¦¹2ÞÍ˜hv—*¬P:Œg¤ÇDï½e¦4[*ä®ª/ÌÝ®JßCäh@z3Fte‰j?iÌ
†7©_Ž]v\5#¸!§û>[ìj¿*“@/PJÜ)†-ôùq„›fIç5ÏT*ÄÑE;—,K;†!iGú”¯ý?.úCf‚Ë“£	PhzAÔL§f¶Lx|ËD•à”U–s0SâÄ´í½CõŽUø
ký}B'9ƒ@+ð'/imZc’ÏQ×rÐ®€*Éß+:‹¥ÒêMLm*7*¤„=´;£—¾C§šu¯"¯ß%qùM+R1ŠQô
IùË"QÛOÑFæÅrpîi‚Í`²’]s¼á~Mtë—cïÅ+¤7É_‰ZmšÛnÉ®•`ˆ\Ù:wO)*øLç'‡ÎæÂ!±7[*ŽE˜,q«p‰ÖªWïÜŽÃÚâ`¿¥oÕ‰dž³˜³Š¥ûÎ
Å«W¥k6e]ˆŸã†‚›ÙH„x¢§^«6]1ÄÎHÇùåoWÚ¶ÉÄµé¯Ž…ÌB¨Qöv””}j—PþÈ÷cp¡²[åÍbT¶Ú¡p	Yð}Ò[Ï ÐÏKAø¡²*/‰eÎÃX°˜97‚¹ÃÀ¸¢7ä]@Œ;ä™…"ô|äëAC>ÔEò‡µëëÓä1?õëIÞÒ‰%ù”‚Ø•~Ì×Œ€Ü¦%èüØŸ°>c4Fñdƒ»Êp\ì*Z’‡æt¦O`g¤u:yE0³F*DŸ,Žk¼HÎ´@ºqù"1>)úUˆ“0_S¼O¨™ÃÛKí-ñ
uh™Gü\Fr×Þ¤Ê¾ù_\æsò©¨ƒ”ºßè'*j+=P
¶hëƒÆdTbxÜŽÃÙ9È~…mr7£<¬JäñÓªÃÿ  rë™«	þKYƒzçØ1FÐèŸ£±pûåÄû9»é8]‘z‡•içãq³kšCuà¿ä%§p
˜QÒ«îS#·Ÿv®Ô–H÷é;ÿ±yëqêûp
Cç½7ýâ'9õ<…U>‹?®Ÿ %¿.œ‘Ÿ!^#õ…Í¸†ÿÕ¼ƒár±’(¸TôfÆuæ5‰KlK;ƒû³)€9œëyú,ÛŸéP°Óúg²Úƒ<
qJÏM…Lp¹j]öÍ.N*í80¹ÁOÚÛg1B=jrq+jäyd*ñ6ûÂuØ~°tI€¶C2é>o©ªÊ˜é!TBª’YÆ¿8÷"Þômµ;µÑê/ÇoðÁHŒ'!a29Ã÷—®œ~-™†®M 0‡°&ƒ°DÜdÍàÉbò(F»?ªa£Z–ã«qÄk?ÂZñj‡**¼¤Xåvá	Ý@µ2÷PðôóÜ7Ü1É>¢Ã„Îðy´‡Tá”™ìE–$©omÚ‰õ
A™ÈñQÂb*×	ƒ™š!¼³Ä«‚J“,ëAÆtR•ø¥CP1¼[á%ÁZ±\kýèuÍß§¬[ÿ±¾ÊçPÐ¶0¼r«¡)t*gOR®ˆåØ´ ×\˜'Ì€ªÃxîŠN¨®AÌ0^IUña&eë\üì]Iƒ‘qáËO=¬`WÜÞêSíŒGUºèHé÷*=zõÌŽ>Â;5(Kú¿|>°Ýñ[“aÌ¡{i°Â;Ž`Öo^µ*Ùðù'+	õ<“²"âµ33Ÿ@‚Rú¨Ü+&‡0ÕF–i>D/
»×Ã·92k½[Éo[Ò€,éãj*Ñ-þ‚¸fE*œ¹y¼øºñ"âd;§G(ßÆéîAµ4Íˆ0;~Ž|“¦É…TIÊ‰Êé½]oq¨ÒŸ©¬vïdÍ…¢*ˆ˜ÉN$©i¾Â·r
tq!Ø›z¯6>P»?C^^ƒÅ÷ŠGDØÝ£ã–>³Ý×B÷„6q^A*mWÌªºè˜‹Å¥T~Þ‡p:P€ÞCŠ	åâ:Lÿjœ/Žy^ÊWèø5Ñcîi'žõÙ˜ì÷Ñžm—Ë9/ž¤;‚Šyñé¡œJò·ø8Š£þ¹TÉRèWJs:e1÷†!‘òÅu£/Ðæ²°€4'J’Œ£#TïYËÔý¸s:—±¥lsì%I]Í~XŠV$—¹èÂÂ:,ggyŸÁ¤‚ég¦I $~/XzÞNlRÅ,SÏ°WÖ˜’‚ZKâƒ`;&ßò2*Q*üxX‰|ÂµçÃø]¯"„³µóþÑéÉ©k3ëfý«P¬ª¿ÞýöÔ=éì}˜4°™ØÃ¶Äo2ˆ‹©{Jï¢H¥*ªµoäî•‹ÓA*4Y}tl€úO‘†Ë”«F%Às¿Uâ|ˆFÝüaùðÔ‰þJ¨v’ªf\¬á0Ú÷c6çÎÜCÊé6¼U…šz£¾§(ú5*ãé.‹³¹µÓÜ'ÝÆï¸öìîRyû‹HQB‰G’î'þQ«\Éà_ÙI<¼&4W;ñ
óRÆ9‰È	YMn8ÄÕ
 Q
Ãîåv¯ƒY9H?r`:`^.²H"*Ám#O
\pÕ
à*WWÝQ^—1?¤¦G«œž)Ò¶ˆE§dË,^¨?˜îd*–xjr(4OØk@ÊóŸü}ÝU“oå¢d¿íxiÒeWSsãÓ£à=Õ§ãæ23LU“F–èeô—OþjÞFü±Ý©GÊLàìð*ëOƒÐƒˆëÝâ>²9G‡p>Á	psŒe¾©Á!Êt2ïÀz)}‚ŸXÙ/¨büN=ò4‰8e›l
öÌ`žëñýD‡ŒÕØ2ñXO[IŽ>*¨²”$œU©ëàŒš³ŸŒA+-Û.f|d,Ó$àÃm8S»Î90¾q®¯½Ù_¤|IiÑï†xa2_¥þP>kM´àKÄa!`A EúßON§ÒäâÿOÅÑ•‰A›çç Ï+ü*\øÖQ5ñúû/Að’|<ç&á`à*ÜkãC°ÄËìïkO”¨ÈþÆý•‘‹Oó…Mi‰rGj%ÏœÜÃ'¨ZbYŽŽ¶†rjq¾þ¦Ò›*,4ÑA#
¤K½~È;´0Õ}¸Ï“nQši*Üß©ê×(~¾7A½¥xãÙ.wgl$¼nøÀê,CYX:Aº¡}¶Æ~/›"î;àoÇd†3!4°Y“Y«óå}Q=™
L<—bßÏŠ¢y¦ùÅˆ4ºCé
’¨ï‹ÁŠ~Œ{„/Òp
Ñ!Xzùme‘—cøAÕLá5ºÊ“³^ù‡I‰î‡‘Ì'È-å!Nö£$É+œ¶×¸ãLEmåÊ<¼¼6‡U|Ž‰·{óâ+uÊßaW ÛÓ*BÓOVË£8uŒqÓµ8·õ{km™´ U[v[A¡ï÷[X/ñgŒ¿Àð,ºwl¨ÕÞ ^KØ[6+,ŽÔc*"6ñª)pöü>»ƒ×GsŒlî µ7êh16 ×"Ã*ˆ²ú1¸zW²ZÓ¥V[˜Ê0€=Þû4˜ßxBwœk/r¬ G¶¾íÉ²Óï–Í :"~£
êJÇ5áQ®'+*½(§px¾íx¦ZWÉ£ºßÒBá¯_c@$1z1ù`==Ñt¤s™JC&@¼çÞU¿—ùÊáö¯ôSjº+hìòîä"n €·õï y°n¹HâG£M9û%á8D=·ºVÿxhnËÉ˜å*nÍqÖ_"1ŽWÇî*îý¦óm›Eµx¦7ÆWç {e‡'£Õ 9*ÝE•ÀŒ¹tèî£F—zP4ý 6aÛ›bÁ]¼ÚÀÞèÚÍ"Šá©•'
¶»§)D¡æŠ¬D5nï6yq…šZ¢OòˆM:À'½|[Ý±Ê'á×Œ·³óÇ
×Üv„GøÈHsÆÔêÂs°ûÀy¼·9µÝ
O~çßè3ÝÄîiB¦Êð4…7ïoŽ[z—¨	.“Í`õ¢æã|§æ_c7¡aŒb¢ùÖòàß['dÜ¤¦£ïè`W€Ùd„b«$³Ê@ŒÆQ›CÈ¢ÛŒ—ÒS<l¤µ£)Ž[×ÖÇÜž	a*)vu'ª3GÜùy`Iöß¹ZŒÇ&yk©>_=”ºeÕôÑôÕ”Ö_ª°5[oNºÁ£û¯X*,œØ0?ßÉ9`Ýsâí-v2›G0\vtzäƒ0{¢L…”§ßiÅpsYFaFæ¿´,Ç>§¼ß*€Q{ÄÐÿ"$hiVwÍ^Ôˆx½Ž `¤Ù*Ÿ‚D*Û"||Š¼*2j6Ó†ú©X&×¸Ç‡zõ—Aæ¸{á´Ü›ùQ,ƒ¢¶_ ø><®(¹Ø×Y%$ºæá×>µ€‰%~ð˜u·Y£ƒØŽÊÉ\ªK67Ñy‰•®]¬G8ß§‚µ8ÄØ[‹O(š§ç¦SîN.Èo&È…ƒ¤x‰“4û—Ò˜*ðµÃíjÙŒLºÍ¸îÛÄ‘íÍ>ŸÄõ€áÉÝìžA?K€÷ÀÒx›Bg¤WÂˆK
¸Ç÷’§í¿L‹³‚n\Ùf—{ak<Ëÿ¾RÇß´XF—(±‰»Ì3O%+«ízh6?$Æ‘Zä‘ŠÄCFŸ&ä·¦*¾£ûÁvvþðAÅlwáü
‡%[§ÌB.!32u*8€%™AÎ"PwÞ’s\
oz'Þã¼®¶æŠÑ~òÓJ‹g.çøÙ`Â:ùG7>Æ`PÑÓÒ Ë	i•P–›”HüÛIµÄ>OKÂ°LŽ³j«§Vç’IÍrçÔ>™w‰ØcJñË&r.ìGù*âÓð»‡rDÏ7Á±:uü2{ÅÜØ´Òð*yz”ò9å.(ÜÉÀ«X¿I'OŽ¶¯bwÙªb¿e#ûXÇ¦q‘FSìáý±®áÞõÔ9ÖklÏ(jÆ+"ûæ ùíè²%Ñ&¦´nté)V‘E,®ë*€~Í#†¨³.E³®Éc‡ÚÿÏ_£Ó*ÄðO•)™¯[ž2@:ŸÖö
…ÃEÙ¨Ö©> ´ÒBâƒ!d8¼º”˜ð8¨wvÌ2€ Aé‹îVÜ‚íêgY‰aEñÌ1û=€u¿€Ë+`PÃa:t^qþ‹Äí©1iÎ*‘ºð‹JUA2¼
#aÇÆv	•Ô—¾³œ'+ÔGöGy]U²m0øv\“ºüŸ³ž¬¬™áhÀàºˆq‰ùçQeêÏŽv˜ñ®á2~9|&ec*úäüi®Z|;ÔÒê+‘¦…þdq»^4þa»“íÐ Â®Ožá:×Tp†*Š5ÈãàRTGd%U(RE-hŒ="@höãa¤á„¢;×ž¿jÜZ!–mrÀ ž—žÕkëw
5)«.føŒ+³²ƒ@ÈµO7ãYv†
%h5cÏˆÞA*—-I°ì/ÇBfI?„èêÚ€@9ÂÑ–*Îc}£›%‘Ã+çQçâ¹ä7‹ð¾t8z˜÷Kf\#Ÿ“òEå¡CéH“&C³?$YªT¬)ês-(í¥ù±½{ú¨o¦xC)Àµyû0ÿ"ú7Æ2ê#?ÔOÉ

Ô–*+‚
#»*‚HÆ/äY¸eIÞe‘™ð"uÔTä±b˜Ô°øEú¼{¡âõ*ÅÀ˜Íñ*°Az·”ÆL@º”äxQôX6
GýçŠ§‚$IŒå¨úÀ>~‰cóÖµH "°F{»S‹è‹)¯›€$¥šõmŽæ‚>/r‘‚fk°P\¦Ú…5C B³áÓ(¾9@*‹æ/…ÀÊ3çå°o ÉbØÕÝÏÈ±ë#kÏmûÜ¸eáå¤(eS ädºÑRg/mª»1«på¹gN€äP’ÒNºEÜâ‰ì>Nâ#ì‡³9xüèõ
ì?0–ƒj™„^l*Õôù–^Äq@Òm_â§R‘Öëh~ð‰ ž—ü2+/*vòid>ÆMeÉ\\ÂÐÐÍÛÈ*¦ƒõQŒÂ{n¤[&Ò'ÓjBsÛž7MŠ5†>òiU†=Ã_M`í=õp
¶æÒPŽÕ\HPtÉ%ÒôŽ§á953¡L¬k5§¯.….zÉzñU¾Uœ®¬çˆWa¹_ÌHýÜúY¿žÆEÃiíõeŽZt
í<@D—Mvøu“ƒ»Åo‘hFƒB3G*ý"ƒ5”´ªbÁUÂpõtVÅARÊJÙ±“¼ÃûõTjˆbðGú<ÃR©f@NTZå;L7¦³Ñ¹‰¥°l÷ø:DAæ¯]ÎÛÜþô”}ÈDÚÏì^Ašó›¨ÉÂ“";¹€´?Ìl:)>(XÀ™zË]¬*Ôª¦…·
uÐw¦C£;ÆùËš{ÜÕè¨æ®_ƒ|É
–f'írmHêmÞ
y÷\E÷ãÙWÚe¿@Ké‚ß«õ‰R{’Ñ¯M[	—¸ÅYw“NŒ‡þdK:€@VX²Ž~æø1äàâÖ-šhµ®‹ÀÇ*r²6Í¥÷¢`©*jw'ûg¿õ(Æ0Ý‹–òAm[F§UåîÆx&?.9ºØˆŽL—°×]½ÌÃ)<ì1Ìé'{Ã£äúþ5SY¾3+6¡^y•}™ Hh¢Åd5Ò}i;+püÜè
aÜØàkß4ÂÉæWp;Jùã*ý?«[œX_ñêæÈ¥¤¦·Þ#*®øXŸXÿTóp$ò-r€£j§Ù[ú:Ô_33ë?K_b6ÓcbÄ#Èo¸Ý’tÈÅy±áã4íÂ¥ù>è¥V}‚Æ§Y©ó‡ê¡qÊ[6‚ÜJ"¬üÂê½ž±êô’ÐÑNäŸÌÓƒ˜Æ%á$Æ±š»âÈ¬kÒF‹‰»0nð‚L¡Úôº»aîb5é6øTŠè\\ŽábÉ³øäzóü8`àžTa7è®SöSùyïâëV«byÓ¦_u³+‘Ïrõb]ð‘æü *øâS_äµÖOÑd……È¢)Kïo$Z¯Ìt_á¿üY®ÿù¸³¡“†h<63;næO}WT’¢Mg•š†ƒ˜!Ä¬ö…œ""›„»ïj¹_™»L(-3RnŒÒ&tº/>u±ªÙ8Ô(§|Uõ¿wÊ-Žñ½A1Ì#÷{G•>ŠøH+ü=¶Fç¡ûg‚Ê€zXk£,±ÝgËÓ{¶u}Ëþ
{V¶4šÈÀkb7å@üd16[ÍãÄ¤Ìu¸ñœë»*Ú£o,©¹_ŽÏIQÚî$fÂü%×áãÌÁž «*°c,áŠß;j—
ßu©Ès‘´y{‹qžÀ]n8dô‰nl¯ãK-á¿*í4HÛdfjK%Œ $•E:}6ÀÈ(s•¿¹vu¼ÈÄ,·éF¾mz~ÕÇÿ®a¦+éu«¥Ä‡¾ÒüYè
ŸÝ=Å“Ó™›ƒ{ÔbçÚZ‡
»*ÑØ(ñõ¦ô
²©

Y'à9® z”pk¿d±™xÎ0Yø4üàÙ½
Œ6R£›ÞªöÈÝ±Ë¸uöY–
ðqËiýŽ
ìŸí©ð—€víÎ„ç·©;Ý¥Ó´ZµX_cz¿†	ÞoÇÃ¶~Iù1c>°«%lDÎ¦gE{¸Ê~å-Mè¾ë°ÊPê>	[Ž®ŸS"t¥¿L3nhÃžDñ»Y`NÕä”Ftƒ®H?Ã‹´GZ·#ÛÅÐh*ìø½)À¯ùÞmô^„5šÄŸTÔéG*É*Îþ½GÄ¿e¡é„ù“Q,~\eu
¶š{»–î#?	O¸6‘³Êeêm˜Kº|u,ºƒ©Y+HÚýÙŸî“f–J…Ç[Ñ ö»½Ú_ðSƒÙ”†£ÀµI§§¹úÌ§‚cri!>Dw}ÜL¤,$QV)‚á	Ì°þ×góíõ¶SßçØr/9ÂÓ`:n“B§$üSäÒ|X„Xùšwjøm”ý#º7¨ú©\7 ö6%õáÜS²Z’E7“åŽX‚yí¢kŽfxfç>Š¼vl"K%ÿåßIv°tZÙBÊqQY™zãGEþØG)Æ",œèêÒ7ë{$Ü^8óæ¹–«rÛ¦Ü4às…ã]ôF ‰ò{+¦Ãplðû·¯¢Ž—qäÜ=KÄ}8¸‰íÜ;ó ,¢ãÝÙ&L-!\XŸ“FÎäð‘4E`¢¬Ä/.<šd OÐ‰÷
¤¢PÌØ©Þ¤¼²y*@rëTÃxwA¦ŸÔ"òR$Bg½û›º#FP«WaÂcìQæ´ :Î˜Ð
&¡üè¢S?/beªC|©jbLóãïMLúËHÞ5O$®’#½=ÛË‚Hž¿É¶_÷%qL€«Ð>[ì¬Ë•G–üƒ–hÔ‘€Ï†~R¸ipw×£f§…ßGOÌµq¼*Íó!8±ƒT
Iœ‹é1ŽÓ‹Ûcgq*û¨Õ•Õ)•p™ø€WþW9Ba*iÇóÐ˜oS`‰íx›
8¤.VŒ÷A&R-gQÏ9¸ÜÃ¯<ÅŒšäµñGÉVTãÖ[ãwb]-	*ŽutnmcQc*pkNí¯^Êô-àì
àAÁŽª2«¡t8‘Ø£ƒŒÁàÃU“á~3UFec€Ú.³è¿¬)óG&dóyö¸ÈÝ[¬Ý#=ÌÒŸ¯}Q%òMÈÇ>u)èÄãÈÇCáoV¼Ÿô„ûñ½ûÅJ#cËöxÁ|ytõ43_hãÌ´ Úë.‚©&×ûc=
’L8ÑGjóo¾o-st/üªI6jtR9³Æw«-²Ï«95jŽmr®”~—8ÁŽ´ŒAÅÐàZ,1]Ó—gÒÆN2~“Ég¨y:Rº¾†£öÉÅ¸šjlV„˜$„ÕyKË¥Ía\äRÑ÷OY^þ¢^I@EÎèOä–é±ÛBNrwT—Ì6ô9X
"¦%Ð×Á…4#}³‘“ù;˜Tm›~Èk’HA3§eÓÝÍ{“È]¢
³¦O—aÙ“5o$‡ûŸ>ù—é-ÝØ“rª°Á´ZüØ'º¯QÞdI [vâ‹îCé7z®ªån‡‘6Æ˜#ÔÇÅ´„.ÚMëo*§×YTÿü
Ä*ØqŸKòî*à¼Æ!i¹ZTºœðepU"®w¹É¢-”kÌ[ G9W²d:5(„á§#IZôôúuVÆ¬c‰õv¶	?Bþ¸ ~D>Ë£–âRk(p÷0^nf†ºã|žšPy1•HN*P¼¢Ó‹K¥‡@

So what do I use to open the file/  Thanks for your response!!:KS> **meierfra. said:**
> Have a look at this how-to:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by meierfra. on 2010-02-13
Don't open that file. Just move it to "C:\" to overwrite your current wubildr.

---

### Post by shadowlands on 2010-02-13
tried it and I still can not boot in to Ubuntu.

---

### Post by meierfra. on 2010-02-13
> tried it and I still can not boot in to Ubuntu.
Darn.That works in almost all cases. Lets have a better look at your setup.

Follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULTS.txt:

---

### Post by shadowlands on 2010-02-14
And I can do this from grub? Not sure how to get the answers you want to help me help my self.silly me i can do this in windows.

---

### Post by shadowlands on 2010-02-14
I down loaded it but what do I use to open it with or how do I get it to

---

### Post by shadowlands on 2010-02-14
I am going to try this agin in the morning.

---

### Post by meierfra. on 2010-02-14
> And I can do this from grub? Not sure how to get the answers you want to help me help my self.silly me i can do this in windows.

Sorry, I was very busy with a different case and forgot to tell you:

You will have to boot from an Ubuntu LiveCD.  Then follow the instruction from the link.

> I am going to try this agin in the morning
Thats' fine. I'll be here.

---

### Post by shadowlands on 2010-02-14
I do not have a live disk.> **meierfra. said:**
> Sorry, I was very busy with a different case and forgot to tell you:

You will have to boot from an Ubuntu LiveCD.  Then follow the instruction from the link.


Thats' fine. I'll be here.

---

### Post by meierfra. on 2010-02-14
> I do not have a live disk.
That will make it difficult to solve your problem.  If you have a CD drive, I suggest to download and burn a LiveCD. If you don't have a CD drive, you should create a LiveUSB.

But let's see whether your are able to manually boot into Wubi:
Try this at the "grub" prompt:


```

linux /vmlinuz root=/dev/[COLOR="Red"]sda1[/COLOR] loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```
You might have to try different values for "sda1". It has to be the device name for the partition containing Wubi. Usually it is "sda1" or "sda2".


**If this boot you into Wubi,** open a terminal in Wubi and type

```
sudo update-grub
```
Reboot and see whether running update-grub solved your problem. If not, boot into Wubi as above, and then  follow the instruction to run the boot_info_script and post the RESULTS.txt


**If you were not able to boot into Wubi,** report any error message you got. Also type

```
ls

set
```

at the "grub>" prompt and post the output.

---

### Post by shadowlands on 2010-02-14
Thanks for comig back to help me.  I am trying the link again to for wubildr and if that does not work I am going with your last suggestion.> **meierfra. said:**
> That will make it difficult to solve your problem.  If you have a CD drive, I suggest to download and burn a LiveCD. If you don't have a CD drive, you should create a LiveUSB.

But let's see whether your are able to manually boot into Wubi:
Try this at the "grub" prompt:


```

linux /vmlinuz root=/dev/[COLOR="Red"]sda1[/COLOR] loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```
You might have to try different values for "sda1". It has to be the device name for the partition containing Wubi. Usually it is "sda1" or "sda2".


**If this boot you into Wubi,** open a terminal in Wubi and type

```
sudo update-grub
```
Reboot and see whether running update-grub solved your problem. If not, boot into Wubi as above, and then  follow the instruction to run the boot_info_script and post the RESULTS.txt


**If you were not able to boot into Wubi,** report any error message you got. Also type

```
ls

set
```

at the "grub>" prompt and post the output.

---

### Post by shadowlands on 2010-02-14
nothing  it says file not founded.

when i type ls in grub I get:  (hd0) (hd,5) (hd0,1)












> **shadowlands said:**
> Thanks for comig back to help me.  I am trying the link again to for wubildr and if that does not work I am going with your last suggestion.

---

### Post by meierfra. on 2010-02-14
> (hd0) (hd,5) (hd0,1)

You have two different partitions. To you know whats on the second partition? I'm asking, since if Wubi is  on a separate partition, you will have to put "wubildr"  on Wubi partition and not on "C:\".

Did your type

```
set
```
at the "grub>" prompt? What was the output?

> nothing it says file not founded.

Boot into Window and look for the folder "C:\ubuntu\disks" . Let me know what is in that folder.

---

### Post by oldefoxx on 2010-02-14
> **shadowlands said:**
> I do not have a live disk.
Excuse me for intruding.  I never waste time trying to figure out what went wrong, because many things can, computers and software being what they are, so I just try to get back to some previous state.  With Ubuntu and other Linux Distros, this means keeping a LiveCD on hand.  It does not mean having to start completely over either, as there are ways to preserve what lies within the /home folder, which is all the user accounts and data.

That said, getting back to a LiveCD download state is easy, because as you indicated, XP still starts up, and you just have to remember the steps you went through previously to get the ISO image and burn it to a CD or DVD, as the case may be.  It has to be a CD-R disk, not a CDRW, because the CD-R holds 50 Mb more than the CDRW, is much faster, and just about all that space is required.

You can also choose to download and use the alternate ISO image, which presents a few different choices as you start up.  It has a recover option as well, but there are no instructions on how to take advantage of this.  The boot process is also more text-based, so you can read what you are doing or choosing as you go along.

If you can't burn a CD or DVD for any reason, then there is still hope.  I am about to post another thread with a bunch of links to where some people have successfully dealt with an image that is on a hard disk partition. not a CD or DVD.  As to setting up your PC to handle this, you still have XP to assist to some extent, and there are versions of Ubuntu that can install and run directly under Windows, which would get you around the lack of a LiveCD temporarily.  You can even look at VMWare Player and VirtualBox, or other VM Manager, and do some of this there.  You have to know what you are doing though, but it is not impossible.  That is why I am offering the links.

Sometimes it is a question of what you really want to do:  Identify the problem, so maybe it can be fixed and not bother others later, or just get around the problem so that you can get on with what you are doing.
I've gone both ways in the past, and it really depends on how much someone else is willing to do and how far they are willing to go to help.  It generally takes an expert to actually nail a problem, and I will work with experts in this regard, but otherwise I might just report a bug and move on by myself.  Your call.

---

### Post by shadowlands on 2010-02-14
in the c drive in the ubuntu file is instal, winboot, ubuntu, uninstall-wubi.> **meierfra. said:**
> You have two different partitions. To you know whats on the second partition? I'm asking, since if Wubi is  on a separate partition, you will have to put "wubildr"  on Wubi partition and not on "C:\".

Did your type

```
set
```
at the "grub>" prompt? What was the output?


Boot into Window and look for the folder "C:\ubuntu\disks" . Let me know what is in that folder.

---

### Post by shadowlands on 2010-02-14
after typong in ls 

(hd0) Hd0,5) hd0,1)

after typing in set
?=0
color_highlight=
pager=
prefix=(hd0,1)/boot/grub
root=hd0,1
show_panic_message=true

> **meierfra. said:**
> That will make it difficult to solve your problem.  If you have a CD drive, I suggest to download and burn a LiveCD. If you don't have a CD drive, you should create a LiveUSB.

But let's see whether your are able to manually boot into Wubi:
Try this at the "grub" prompt:


```

linux /vmlinuz root=/dev/[COLOR="Red"]sda1[/COLOR] loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```
You might have to try different values for "sda1". It has to be the device name for the partition containing Wubi. Usually it is "sda1" or "sda2".


**If this boot you into Wubi,** open a terminal in Wubi and type

```
sudo update-grub
```
Reboot and see whether running update-grub solved your problem. If not, boot into Wubi as above, and then  follow the instruction to run the boot_info_script and post the RESULTS.txt


**If you were not able to boot into Wubi,** report any error message you got. Also type

```
ls

set
```

at the "grub>" prompt and post the output.

---

### Post by shadowlands on 2010-02-14
sudo update-grub 

message "Error: unknown command 'sudo'"

---

### Post by Easy Limits on 2010-02-14
Is your computer 32-bit and Wubi is trying to install a X64 version of Ubuntu?  This happened to me.  Fortunately, I had a i386 ISO on hand.

---

### Post by shadowlands on 2010-02-14
how do i find out what it is. I think it is 32.> **Easy Limits said:**
> Is your computer 32-bit and Wubi is trying to install a X64 version of Ubuntu?  This happened to me.  Fortunately, I had a i386 ISO on hand.

---

### Post by Easy Limits on 2010-02-14
Do you know what processor (CPU) you have in your computer?  If not, can you log in to Windows and check in the device manager?

---

### Post by shadowlands on 2010-02-14
it is a 32 bit ( thank you google gods!!)
> **Easy Limits said:**
> Do you know what processor (CPU) you have in your computer?  If not, can you log in to Windows and check in the device manager?

---

### Post by Easy Limits on 2010-02-14
You will need to download the i386 (32 bit) version of Ubuntu.

---

### Post by meierfra. on 2010-02-14
> in the c drive in the ubuntu file is instal, winboot, ubuntu, uninstall-wubi.

"ubuntu file"?  Do you have an "ubuntu" folder on the C:drive?

---

### Post by shadowlands on 2010-02-14
Yes, yes i do !!> **meierfra. said:**
> "ubuntu file"?  Do you have an "ubuntu" folder on the c:drive?

---

### Post by meierfra. on 2010-02-14
But you don't have a folder with the name "disks" inside the ubuntu folder?
Then something went seriously wrong during the installation.

---

### Post by shadowlands on 2010-02-14
no folder with disk in side of it.> **meierfra. said:**
> But you don't have a folder with the name "disks" inside the ubuntu folder?
Then something went seriously wrong during the installation.

---

### Post by Easy Limits on 2010-02-14
Yes, you do if you used Wubi.

---

### Post by meierfra. on 2010-02-14
I suggest to uninstall Wubi from "Add/Remove" program and try  again. 

You might consider doing a regular Ubuntu install instead of Wubi.  The only reason to use Wubi is that Wubi is easier to install. Once you have problems installing Wubi, you might as well install Ubuntu.

---

### Post by shadowlands on 2010-02-14
kay the folder labeled Ubuntu in the "c" drive has four folder in side of it 1. install 2. winboot 3. ubuntu 4. uninstall-wubi.> **Easy Limits said:**
> Yes, you do if you used Wubi.

---

### Post by Easy Limits on 2010-02-14
If you click on the Wubi installer you can un-install Ubuntu.  The Wubi will delete everything.  Or, you can Add/Remove programs in the control panel.

---

### Post by shadowlands on 2010-02-14
Then How will I run the program is there no way to save this with out having to start over?  I am starting to hate karmic wiath a passion. It has more bugs than the out doors!!

---

### Post by Easy Limits on 2010-02-14
It's not really a Karmic problem but a Wubi problem.

I think you will find doing a fresh install of Ubuntu with a Live CD on a clean partition will brighten your day.

---

### Post by meierfra. on 2010-02-14
> Then How will I run the program is there no way to save this with out having to start over? 

One thing I forgot to ask.   Is this a fresh install?  Or did you already run Wubi for a while? To you have any data on Wubi you need to rescue?

If this is a fresh install,  starting from scratch is your best options.
If its not a fresh install,  we  might try to rescue your data, but I don't have much hope.


>  1. install 2. winboot 3. ubuntu 4. uninstall-wubi.
What is inside "3. ubuntu"?

---

