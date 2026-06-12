---
title: "SSH tunnel bandwidth overhead"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by NTolerance on 2008-07-14
I'm using an SSH tunnel to stream mp3s from a remote HTTP server.  I'm just wondering what sort of bandwidth overhead an SSH tunnel imposes when used as opposed to a conventional connection to the HTTP server.

---

### Post by NTolerance on 2008-07-15
bump for curiosity

---

### Post by tamoneya on 2008-07-15
i dont think(feel free to correct me) ssh has much overhead bandwidth.  It is transferring more or less the same amount of data but just in an encrypted form.  The main over head of SSH lies in the encrypting and decrypting of the data which is an overhead on the CPU.  Still given most of the computers today with high clock rate multicore processors it isnt an issue most of the time.

---

### Post by NTolerance on 2008-07-15
Excellent, thanks.  One wonders why anyone bothers opening ports on routers when SSH tunnels work so well.

---

### Post by tamoneya on 2008-07-15
an ssh tunnel still requires an open port and it requires that computer authenticate with each other and exchange keys.  For many protocols this doesnt make any sense and is totally unnecessary.

---

### Post by NTolerance on 2008-07-15
> **tamoneya said:**
> an ssh tunnel still requires an open port and it requires that computer authenticate with each other and exchange keys.  For many protocols this doesnt make any sense and is totally unnecessary.

I was mainly referring to personal use such as mp3 streaming, mythweb access, file transfer, etc...  After getting QoS tweaked on my router I've been able to eek every last bit per second out of my 384kb/sec upload and can usually stream 320kbps mp3s without interruption.  :guitar:

---

### Post by weazzle on 2008-10-01
> **tamoneya said:**
> i dont think(feel free to correct me) ssh has much overhead bandwidth.  It is transferring more or less the same amount of data but just in an encrypted form.  The main over head of SSH lies in the encrypting and decrypting of the data which is an overhead on the CPU.  Still given most of the computers today with high clock rate multicore processors it isnt an issue most of the time.

Actually, SSH does add some overhead to the packet. SSH has its own packets into which it wraps data before handing it off for TCP/IP encapsulation. This packet contains length (4 bytes), padding length (1 byte), data section (depends on MTU), padding(4-255 bytes), and Message Authentication Code (length varies, probably 20 bytes or less).

Max MTU is 1500 bytes, you lose 66 bytes due to encapsulation (header information). This leaves you with 1434 bytes unencrypted. When using ssh encryption, worst case scenario uses around 380 bytes, cutting you down to 1054 bytes of actual data.

Keep in mind this is worst case, but there is always some overhead.

---

