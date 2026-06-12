---
title: "No puedo navegar..."
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by areku on 2005-03-27
Hola. Bueno, ahora instale Warty en mi pc y pues todo halo muy bien. pero al ratito el internet dejó de funcionar y en el momento en el que me funciono estaba muy lento. Entonces lei en el foro que tenia que modificar la linea 21 del archivo dhclient.conf, despues del netbios-netscope tenia ke ponerle coma antes del interface-mtu. pero en mi archivo no sale interface-mtu. Ya lo puse y no paso nada.. entonces no se como hacerlo funcionar y la vdd es mucha lata tener que volver a bajar la version nueva para poder modificar eso... 
Si alguien puede poner  el archivo dhclient.conf completo en este post para poder verlo y comparar y mejor si alguien ke tenia esta version tubo el problema y ya lo arreglo....

por favor ayuden.. me pasaba lo mismo con debian.... y no quiero volver a windows....  gracias.

---

### Post by bored2k on 2005-03-28
[QUOTE=areku]Hola. Bueno, ahora instale Warty en mi pc y pues todo halo muy bien. pero al ratito el internet dejó de funcionar y en el momento en el que me funciono estaba muy lento. Entonces lei en el foro que tenia que modificar la linea 21 del archivo dhclient.conf, despues del netbios-netscope tenia ke ponerle coma antes del interface-mtu. pero en mi archivo no sale interface-mtu. Ya lo puse y no paso nada.. entonces no se como hacerlo funcionar y la vdd es mucha lata tener que volver a bajar la version nueva para poder modificar eso... 
Si alguien puede poner  el archivo dhclient.conf completo en este post para poder verlo y comparar y mejor si alguien ke tenia esta version tubo el problema y ya lo arreglo....

por favor ayuden.. me pasaba lo mismo con debian.... y no quiero volver a windows....  gracias.[/QUOTE]
 Lo primero es que en los forums , en sus reglas [http://ubuntuforums.org/faq.php?](http://ubuntuforums.org/faq.php?) dicen claramente que esta prohibido el uso de otro lenguaje que no fuese ingles.

In english -> first of all, the rules of the forums state that we must speak in english only. Not leet, not spanish, english only.

---

### Post by telmo on 2005-03-28
Es verdad! :)
It's true! :)

---

### Post by bored2k on 2005-03-28
[QUOTE=telmo]Es verdad! :)
It's true! :)[/QUOTE]
 Weird thing is, if the dude managed to post and read other threads, he knows proper english ..

---

### Post by areku on 2005-03-28
oks, sorry... 

Hi, today i install warty in my PC, and everything was well, but later i can't connect to internen. i read that the problem was in line 21 of the file dhclient.conf and i need to put a comma between netbios-scope and interface-mtu:

'
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name,
netbios-name-servers, netbios-scope, interface-mtu;
'
but in my file doesnt appear interface-mtu. so i put it and save but nothing happened...


what happend in this version of ubuntu?
what i need to do?

---

### Post by areku on 2005-03-28
[QUOTE=bored2k]Weird thing is, if the dude managed to post and read other threads, he knows proper english ..[/QUOTE]

the problem is i can read but i can't write....

---

### Post by telmo on 2005-03-28
LOL
you're writing is just fine! I'm from Portugal, and hey...  ;) don't worry, bored2k ain't kickin' u! :)

---

### Post by bored2k on 2005-03-28
> **telmo]LOL
you're writing is just fine! I'm from Portugal, and hey...   said:**
> 
 No I'm not. I can not even do that .

[QUOTE]WE ASK THE USERS ON THE UBUNTUFORUMS TO PLEASE FOLLOW THE UBUNTU CODE OF CONDUCT and....

3. Try to make your postings understandable, we have users from all over the world and not all of us are fluent in every language.

Remember:

    * Write in English the best you can.


And P.S. - I'm usually not this big of an a$$ ;) .

---

### Post by areku on 2005-03-28
then... Who knows how i can fix my problem?? 

 [-o<

---

