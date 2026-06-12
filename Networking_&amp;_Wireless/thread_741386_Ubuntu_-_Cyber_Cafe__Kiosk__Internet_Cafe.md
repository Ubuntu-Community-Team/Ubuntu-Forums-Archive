---
title: "Ubuntu - Cyber Cafe / Kiosk / Internet Cafe"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by jorgerosa on 2008-03-31
Hello all, im trying to create a [COLOR=RoyalBlue]**SMALL CYBER CAFE**[/COLOR], with 5 client machines and 1 server, and i want to use [COLOR=RoyalBlue]**ONLY**[/COLOR] open source / free software over our loved Ubuntu Linux.
So the copies of MS Windows Vista OEM in that machines have been trow away, now...
After googled i found a [COLOR=RoyalBlue]**kde-kiosk**[/COLOR] but NOT a [COLOR=RoyalBlue]**gnome-kiosk**[/COLOR] or so... :( ...no problem, soon or later will be one out there ;)
 
> I think would be nice to bring something new, and useful, to our Ubuntu, in this area, right?
> I´ll post here the tutorials and good links (downloads, lan managers, etc, etc) that i´ll find on my way. Please help here, guys. Thanks.
 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[B]
SOFTWARE:[/B]

> I found these in **freshmeat.net**: [http://freshmeat.net/search/?q=internet+cafe&section=projects](http://freshmeat.net/search/?q=internet+cafe&section=projects)
 > Found in **sourceforge**: [http://sourceforge.net/search/?words=internet+cafe&sort=score&sortdir=desc&offset=0&type_of_search=soft&pmode=0&form_cat=18](http://sourceforge.net/search/?words=internet+cafe&sort=score&sortdir=desc&offset=0&type_of_search=soft&pmode=0&form_cat=18)
> **LanBR** Seems to me to be the best lan manager around (according to forums, blogs, etc.): [Images]("http://images.google.pt/images?hl=pt-PT&q=lanbr&btnG=Procurar+imagens&gbv=2"), [Downloads]("http://www.portalcriativa.com.br/Downloads.html"),  [LanBR Server (Ubuntu is there) Tutorial]("http://www.portalcriativa.com.br/LanBr-tec.html#Serv_Requisitos"),  [LanBR Client Tutorial]("http://www.portalcriativa.com.br/LanBr-tec.html#Cli_instalacao")
> **LanOS** (Ready pre compiled linux for lan houses, based on [SIZE=-1][COLOR=#000000]Linux Ubuntu 7.10[/COLOR][/SIZE]): [link]("http://www.portalcriativa.com.br/LanOS6R.html"), [video]("http://br.youtube.com/watch?v=rFNLtEqWIHA")
(Sorry, but the most links are in Portuguese idiom, i will try to find in english also, but no luck until now...)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[B]
TUTORIALS and TALKING about:

[/B]> My friend Coringao ([Ubuntu Games]("http://www.ubuntugames.org/en/UbuntuGames") Manager) has a post here about this (in Portuguese only): [http://coringao.wordpress.com/2008/03/05/lan-house-utilizando-ubuntukubuntu/](http://coringao.wordpress.com/2008/03/05/lan-house-utilizando-ubuntukubuntu/)
> Tutorial (in portuguese only): [http://ubuntupedia.info/index.php/Criar_um_caf%C3%A9_Internet_em_Ubuntu_Linux]("http://ubuntupedia.info/index.php/Criar_um_caf%C3%A9_Internet_em_Ubuntu_Linux")
> Screenshots: [http://www.guls.com.br/index.php?p=cyberup&t=cyber-cafe-com-linux](http://www.guls.com.br/index.php?p=cyberup&t=cyber-cafe-com-linux)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Btw, i just found that to install games in a lan (cyber cafe or kiosk), besides the game cost, you have to pay monthly fees! (eg. Valve Half Life, Counter Strike, etc, etc.)
This doesnt happen in mostly Linux Open Source Games, of course.

---

### Post by dmizer on 2008-03-31
found these two helpful threads just by searching the forums for "cyber cafe":

[http://ubuntuforums.org/showthread.php?t=621320](http://ubuntuforums.org/showthread.php?t=621320)

[http://ubuntuforums.org/showthread.php?t=617483](http://ubuntuforums.org/showthread.php?t=617483)

i recall frequently seeing people employing ubuntu in cyber/internet cafes, so there should be lots of information for you in the forums here.

---

### Post by mwero001 on 2008-04-09
Hi,
Did you limit the bandwidth to each machine? If you did, please explain how.

---

### Post by BatsotO on 2008-04-16
I Run ubuntu cyber-cafe too, naybe this could help

For desktop lock you could try pessulus that's the best thing available for gnome right now, and some knowledge about gconf-editor.
Secure your client, disable terminal (gnome-terminal & xterm) by chmod o-x gnome-terminal (this off course will depend on the level of security you need, mainly if you want to prohibit your user from killing critical task such as billing application. And secure the other application you see necessary.
For 5 client, I think you'll only need a decent router. Some old pc will do the job fine (mine was some p2 and celerons) and for 5 client I personally think you wont need to limit any bandwidth. Basically I run 5 year old RH for router as gateway router for at least 10 pcs, and the speed in every pc not much different, been with vsat and adsl connection, no major issue.

And forget ltsp or any thin client, your user want bleeding fast pc as they can get, I've done that, Max a p4 server can handle thin clients are 6-7 clients, and with full user, all of them opening firefox and open office, the server could go freeze at anytime, bringing all the clients with it.

What spec do you plan for clients? coz if you can get some 3d accelerated vga you can go compiz, and that a plus.

for billing system, there's cclfox nice program, though need some more improvement. cclfox can handle timer, membership, prepaid and point of sale.

hope this help, i like to see more ubuntu cyber cafe, we sure need to do more talk.

---

