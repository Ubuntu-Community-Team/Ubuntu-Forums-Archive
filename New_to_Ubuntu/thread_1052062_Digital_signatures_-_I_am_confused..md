---
title: "Digital signatures - I am confused."
date: 2009-01-27
forum: New to Ubuntu
---

### Post by ProgramErgoSum on 2009-01-27
I just want to e-mail a digitally signed document. Here is what I have tried but don't quite follow.

[LIST=1]
[*]Right-click on the document and select 'Sign'. But, that creates a detached file. I don't want separate files.
[*]Use gpg from command line and use the -s option to sign the document. That creates a .gpg file which offers decryption whereas I had only signed not encrypted. Why ?
[*]Inserting digital signature from Open Office. This would not work because it is not able to locate the signature because Firefox does not have it. Why should OOo mandate that the certificate be with browser ? I [figured that one]("http://wiki.services.openoffice.org/wiki/How_to_use_digital_Signatures")...but, really, is it not possible to point it to what I am having now ?
[/LIST]

The last point above brings me to another question. In my first attempt at digital signatures, I was prompted to create the keys. I am not able to locate them nor create a new pair. How do I create them ?

---

### Post by sandyd on 2009-01-27
why don't you just generate a key with openssl and sign the entire email with thunderbird?

gpg keys, take a look @ this :[http://madboa.com/geek/gpg-quickstart/](http://madboa.com/geek/gpg-quickstart/)

openssl keys take a look@ this: [http://madboa.com/geek/openssl/](http://madboa.com/geek/openssl/)

---

### Post by sarpulhu on 2009-01-27
Try Applications -> Accessories -> "Passwords and Encryption keys"
It will help make GPG keys

---

### Post by sarpulhu on 2009-01-27
Oh and by right clicking you should be able to sign and check the file by right clicking in the file browser or desktop. The signature file is SEPERATE from the actual file and can be added as an attachment in your email. The sig file is used to check the other file. Try changing the file after you sign it then check the signing and it will say forged. Hope that helps.

---

### Post by ProgramErgoSum on 2009-01-27
Sending the document is not *the* issue here. I might copy into his USB, or make it available on a server, etc.

Basically, what I want to know is, how do I sign a doc digitally and yet have a single file at the end (as shown below - taken from wikipedia) ? [IMG]http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg[/IMG]

Thanks for the navigation path to keys !

[http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg](http://en.wikipedia.org/wiki/File:Digital_Signature_diagram.svg)

---

### Post by sarpulhu on 2009-01-27
I think the diagram might be confusing. I think that by adding literally the signature to the document you have changed the hash used to sign it. They "attached and not merged it" You could create a single file into a zip, gz, file etc. Then extract to get the document and the "seal". Remember that the destination person will need your public key to check it.

---

### Post by ProgramErgoSum on 2009-01-28
> They "attached and not merged it" You could create a single file into a zip, gz, file etc.

That's right and that is how interpreted too. And, yes, I could zip them into a single file. 

But, I always believed that, a digitally signed document was a document plus the signature; not two separate entities. After all, a digitally signed document in OOo or in MS is a singular entity (the presence of signature shown by the red seal). Why can't I do the same with other files (command line or otherwise) ?

---

