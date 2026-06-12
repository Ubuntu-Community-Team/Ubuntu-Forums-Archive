---
title: "OS from usb"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by c0nrad on 2010-05-10
Hey,

I'm trying to create a simple OS to help me learn asm a little better, but I'm not quite sure how to get it to boot. I found the following code online:

easyos.asm
```

[BITS 16]
[ORG 7C00h]
main:
mov ah,0Eh
mov al,'a'
int 10h
times 510-($-$$) db 0
dw 0xAA55
```Then I used nasm:
```

nasm easyos.asm -o os.bin

```And this is where I'm having a hard time, I want to put it on my flash drive, so i tried:
```

dd if=os.bin of="usb location"

```I restarted my computer and booted from flash drive and nothing happened.

I'm guess the dd command wasen't the right choice.

If anyone know something else that worked that'd be great.

Thanks,
C0nrad

---

### Post by 3rdalbum on 2010-05-10
The computer doesn't just execute code that's sitting on an unformatted flash drive. You need some other code around it as a kind of bootloader. This is outside my sphere of knowledge though.

---

