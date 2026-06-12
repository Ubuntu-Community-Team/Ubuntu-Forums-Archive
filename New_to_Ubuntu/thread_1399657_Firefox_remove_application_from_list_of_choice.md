---
title: "Firefox: remove application from list of choice"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by marty1011 on 2010-02-05
Hello everyone,

I have a small question. How do I remove an application of the list of applications to use in firefox. Here is a detailed scenario: I wanted to play songs from Last.fm using banshee so I manually added banshee to the list by clicking on the choose button and navigating to /usr/bin/banshee . Now I want to delete banshee from the list of applications. I do I accomplish this?

Many thanks in advance and also Thank You for reading my poor english.

Regards, 
marty

---

### Post by lovinglinux on 2010-02-06
The easiest way is to close Firefox and delete the file *mimeTypes.rdf* from your Firefox profile folder, which is located under ~/.mozilla/firefox/<*profilename*>. Unfortunately, this will completely reset all your application settings.

Alternatively, you can open that file and edit manually. Keep in mind it might have more than one instance of an application. For example, this is what I got after adding smplayer as the default player for AU file on a clean profile:

```
  <RDF:Description RDF:about="urn:mimetype:externalApplication:audio/basic"
                   NC:prettyName="smplayer"
                   NC:path="/usr/bin/smplayer" />
```

```
    <NC:possibleApplication RDF:resource="urn:handler:local:/usr/bin/smplayer"/>
```

```
  <RDF:Description RDF:about="urn:handler:local:/usr/bin/smplayer"
                   NC:prettyName="smplayer"
                   NC:path="/usr/bin/smplayer" />
```

---

### Post by marty1011 on 2010-02-06
Thanks a lot. That solution worked perfectly. :D

Regards,

marty

---

