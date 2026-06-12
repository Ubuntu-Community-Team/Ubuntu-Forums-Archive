---
title: "Can't resize filesystem - problem with resize2fs"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Minolas on 2009-01-12
I have a persistence file which I am trying to enlarge.

I did

```

dd if=/dev/zero of=/tmp/tempfile bs=1M count=800

```

Then I did :
```

cat /tmp/tempfile >> /media/USBDRIVE/casper-rw

```

Now I tried to enlarge the file system to encompass the added disk space:

```
e2fsck -f /media/USBDRIVE/casper-rw
```
Worked fine

But then when I try
```
resize2fs /media/USBDRIVE/casper-rw
```
It keeps telling me:
Please run 'e2fsck -f /media/UBUNTULIVE/casper-rw' fist.

But I DID run it first. And tried to run it again and again, it found no problems yet resize2fs insists on not working :(

---

### Post by Minolas on 2009-01-12
anyone :confused:

---

### Post by ibuclaw on 2009-01-12
Not even:
```
sudo e2fsck -f -y -v /media/USBDRIVE/casper-rw
```
Can fix it?

Regards
Iain

---

### Post by Minolas on 2009-01-12
I solved it. The e2fsck was an older version than the resize2fs so the resize2fs didn't recognize e2fsck already checked the device. so working now.

---

### Post by Endolith on 2009-06-16
What do you mean it's an older version?  The versions packaged with Ubuntu are not compatible with each other?

---

### Post by Clorow on 2009-06-16
This doesn't really seem like "absolute beginner talk"... ;)

Would this be appropriate on another board?

---

### Post by cyberchango on 2009-07-13
I'm having the same problem, where did you find the "correct" version??..
HELP.. I'm really a beginner..

---

### Post by renbla on 2009-07-13
> **Clorow said:**
> This doesn't really seem like "absolute beginner talk"... ;)

Would this be appropriate on another board?

+1

It's true :(. It took me a quite long time reading man to understand what you are saying ;).

---

### Post by cyberchango on 2009-07-13
rodrigo@ubuntu:~/e2fsprogs-1.41.7/build$ e2fsck -f /media/disk/casper-rw
e2fsck 1.41.7 (29-June-2009)
Paso 1: Verificando nodos-i, bloques y tamaños
Paso 2: Verificando la estructura de directorios
Paso 3: Revisando la conectividad de directorios
Paso 4: Revisando las cuentas de referencia
Paso 5: Revisando el resumen de información de grupos
/media/disk/casper-rw: 5106/129024 ficheros (11.3% no contiguos), 515838/515892 bloques
rodrigo@ubuntu:~/e2fsprogs-1.41.7/build$ resize2fs /media/disk/casper-rw 
resize2fs 1.41.7 (29-June-2009)
Por favor ejecute antes 'e2fsck -f /media/disk/casper-rw'.

Ok, I'M a beggines, as you can see, they are both the same version, but, still the same problem.

---

