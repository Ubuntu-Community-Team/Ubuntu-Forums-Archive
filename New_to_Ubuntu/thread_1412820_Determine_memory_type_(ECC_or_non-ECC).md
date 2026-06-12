---
title: "Determine memory type (ECC or non-ECC)"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by mataug on 2010-02-21
I need to purchase RAM for my desktop and need to confirm if the current RAM is ECC or non-ECC (I read on crucial.com that mixing ECC & non-ECC memory is not recommended).

Is there a way that one is able to determine the type within Ubuntu ? I'm aware that a look at the RAM chip can tell you that but am not sure if it could be done via the OS also.

I came across a command on this forum - dmiencode
I have attached the output of that in a text file. However I cannot make head or tail out of it wrt memory type except the fact that that there are two 512 RAM chips there.

Thanks

---

### Post by paydaydaddy on 2010-02-21
You can most likely look up memory requirements by computer brand/model or motherboard make/model. It is doubtful that you have ecc (error correction code/circuitry) memory as it is generally reserved for use in servers or other "mission critical applications".
I believe that memtest will tell you if you have ecc memory.

---

### Post by mataug on 2010-02-21
this is the best that I could find on dell's website -
[http://www.dell.com/downloads/us/products/precn/ws360_spec.pdf](http://www.dell.com/downloads/us/products/precn/ws360_spec.pdf)

from what I could make out from the spec, both ECC and non-ECC seemed okay for the system but I was unable to determine the type on the one that I currently have

thanks

---

### Post by paydaydaddy on 2010-02-21
You do know how to run memtest?

---

### Post by tadcan on 2010-02-21
I can't tell from the file.

However, EEC code was a part of SD ram. With DDR ram it was no longer needed, so if you have a new machine you don't need EEC.

---

### Post by mataug on 2010-02-21
> **paydaydaddy said:**
> You do know how to run memtest?

I'm not aware of how to run it from remote login

---

### Post by paydaydaddy on 2010-02-21
> **mataug said:**
> I'm not aware of how to run it from remote login
So, you do not have physical access to the machine in question?

---

### Post by baltadt on 2010-02-21
It is usually easier to replace the memory with the same type. With that said when I upgrade I usually replace all the sticks and get rid of the old ones. That way you know the case latency is the same and you will not run into any problems in the long run. I always say it is like replacing headlights on a car, don't do just one.

---

### Post by mataug on 2010-02-21
> **paydaydaddy said:**
> So, you do not have physical access to the machine in question?

not until tomorrow morning ... I was planning to open the CPU anyways but the main motive behind me creating this thread was to know if Ubuntu(or any OS in general) can provide the required information

---

### Post by paydaydaddy on 2010-02-21
post the output of this code

```
dmidecode --type 5,6,16,17
```

---

### Post by mataug on 2010-02-21
> **paydaydaddy said:**
> post the output of this code

```
dmidecode --type 5,6,16,17
```

I get the following(have also attached a txt file with the output in it) -

> # dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Single-bit ECC
	Maximum Capacity: 4 GB
	Error Information Handle: No Error
	Number Of Devices: 4

Handle 0x1100, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL A DIMM 0
	Bank Locator: Not Specified
	Type: SDRAM
	Type Detail: Synchronous
	Speed: 400 MHz (2.5 ns)

Handle 0x1101, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL B DIMM 0
	Bank Locator: Not Specified
	Type: SDRAM
	Type Detail: Synchronous
	Speed: 400 MHz (2.5 ns)

Handle 0x1102, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL A DIMM 1
	Bank Locator: Not Specified
	Type: SDRAM
	Type Detail: Synchronous
	Speed: 400 MHz (2.5 ns)

Handle 0x1103, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: CHANNEL B DIMM 1
	Bank Locator: Not Specified
	Type: SDRAM
	Type Detail: Synchronous
	Speed: 400 MHz (2.5 ns)



thanks

---

### Post by paydaydaddy on 2010-02-21
So, it appears that it is ecc memory.

---

### Post by mataug on 2010-02-21
is it because of this ?
> Error Correction Type: Single-bit ECC

---

### Post by paydaydaddy on 2010-02-22
> **mataug said:**
> is it because of this ?
Yes, that is what you are looking for. Here is the (partial) output from my computer with non-ecc memory for comparison.

Handle 0x0028, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

---

### Post by mataug on 2010-02-22
> **paydaydaddy said:**
> Yes, that is what you are looking for. Here is the (partial) output from my computer with non-ecc memory for comparison.

Handle 0x0028, DMI type 16, 15 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: None
        Maximum Capacity: 4 GB
        Error Information Handle: Not Provided
        Number Of Devices: 2

ouch! I was so far looking online for non-ECC memory and a 2 GB kit(2*1GB) was around $80. The price for the same RAM but ECC is around $135 :(

---

### Post by mataug on 2010-02-22
so I opened up the CPU, pulled out the RAM and you were right my friend

both of them read - 512MB, DDR, 400, CL3, ECC

thanks for the help

---

