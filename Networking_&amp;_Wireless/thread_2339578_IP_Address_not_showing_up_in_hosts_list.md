---
title: "IP Address not showing up in hosts list"
date: 2016-10-10
forum: Networking &amp; Wireless
---

### Post by mirukai on 2016-10-10
Hi all!

I am having issues with my Ubuntu 16.04 machine. When I started working on my old PC to set it up, I was given this when running ifconfig. I have shortened the output to the relevant areas.
```
enp2s0    Link encap:Ethernet  HWaddr b8:ac:6f:19:e4:8d            inet addr:192.168.0.155  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6029:8bb1:8a79:514c/64 Scope:Link
          inet6 addr: 2a02:c7f:9626:1800:281b:60eb:bf22:1511/64 Scope:Global
          inet6 addr: fd63:1a6c:a4e2:0:281b:60eb:bf22:1511/64 Scope:Global
          inet6 addr: 2a02:c7f:9626:1800:c589:67f7:8c27:8949/64 Scope:Global
          inet6 addr: fd63:1a6c:a4e2:0:5ee2:215b:81b9:8d67/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:822000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1203275602 (1.2 GB)  TX bytes:23022396 (23.0 MB)
          Interrupt:16
```

However when running "nmap -sL 192.168.0.155/24", 192.168.0.155 doesn't show up, as seen here.
```
mirukai@hayden-pc:~$ nmap -sL 192.168.0.155/24

Starting Nmap 7.30SVN ( https://nmap.org ) at 2016-10-10 16:14 BST
Nmap scan report for 192.168.0.0
Nmap scan report for SkyRouter.Home (192.168.0.1)
Nmap scan report for Client (192.168.0.2)
Nmap scan report for 192.168.0.3
Nmap scan report for UNKNOWN (192.168.0.4)
Nmap scan report for 192.168.0.5
Nmap scan report for 192.168.0.6
Nmap scan report for TK421 (192.168.0.7)
Nmap scan report for 192.168.0.8
Nmap scan report for 192.168.0.9
Nmap scan report for 192.168.0.10
Nmap scan report for 192.168.0.11
Nmap scan report for 192.168.0.12
Nmap scan report for 192.168.0.13
Nmap scan report for BONEY (192.168.0.14)
Nmap scan report for 192.168.0.15
Nmap scan report for 192.168.0.16
Nmap scan report for 192.168.0.17
Nmap scan report for 192.168.0.18
Nmap scan report for 192.168.0.19
Nmap scan report for 192.168.0.20
Nmap scan report for 192.168.0.21
Nmap scan report for 192.168.0.22
Nmap scan report for 192.168.0.23
Nmap scan report for 192.168.0.24
Nmap scan report for 192.168.0.25
Nmap scan report for 192.168.0.26
Nmap scan report for 192.168.0.27
Nmap scan report for 192.168.0.28
Nmap scan report for 192.168.0.29
Nmap scan report for 192.168.0.30
Nmap scan report for 192.168.0.31
Nmap scan report for 192.168.0.32
Nmap scan report for 192.168.0.33
Nmap scan report for 192.168.0.34
Nmap scan report for 192.168.0.35
Nmap scan report for 192.168.0.36
Nmap scan report for 192.168.0.37
Nmap scan report for 192.168.0.38
Nmap scan report for 192.168.0.39
Nmap scan report for 192.168.0.40
Nmap scan report for 192.168.0.41
Nmap scan report for 192.168.0.42
Nmap scan report for 192.168.0.43
Nmap scan report for 192.168.0.44
Nmap scan report for 192.168.0.45
Nmap scan report for 192.168.0.46
Nmap scan report for 192.168.0.47
Nmap scan report for 192.168.0.48
Nmap scan report for 192.168.0.49
Nmap scan report for 192.168.0.50
Nmap scan report for 192.168.0.51
Nmap scan report for 192.168.0.52
Nmap scan report for 192.168.0.53
Nmap scan report for 192.168.0.54
Nmap scan report for 192.168.0.55
Nmap scan report for 192.168.0.56
Nmap scan report for 192.168.0.57
Nmap scan report for 192.168.0.58
Nmap scan report for localhost (192.168.0.59)
Nmap scan report for 192.168.0.60
Nmap scan report for 192.168.0.61
Nmap scan report for 192.168.0.62
Nmap scan report for 192.168.0.63
Nmap scan report for 192.168.0.64
Nmap scan report for 192.168.0.65
Nmap scan report for 192.168.0.66
Nmap scan report for 192.168.0.67
Nmap scan report for 192.168.0.68
Nmap scan report for 192.168.0.69
Nmap scan report for 192.168.0.70
Nmap scan report for 192.168.0.71
Nmap scan report for 192.168.0.72
Nmap scan report for 192.168.0.73
Nmap scan report for 192.168.0.74
Nmap scan report for 192.168.0.75
Nmap scan report for 192.168.0.76
Nmap scan report for 192.168.0.77
Nmap scan report for 192.168.0.78
Nmap scan report for 192.168.0.79
Nmap scan report for 192.168.0.80
Nmap scan report for 192.168.0.81
Nmap scan report for 192.168.0.82
Nmap scan report for 192.168.0.83
Nmap scan report for 192.168.0.84
Nmap scan report for 192.168.0.85
Nmap scan report for 192.168.0.86
Nmap scan report for 192.168.0.87
Nmap scan report for 192.168.0.88
Nmap scan report for 192.168.0.89
Nmap scan report for 192.168.0.90
Nmap scan report for 192.168.0.91
Nmap scan report for 192.168.0.92
Nmap scan report for 192.168.0.93
Nmap scan report for 192.168.0.94
Nmap scan report for 192.168.0.95
Nmap scan report for 192.168.0.96
Nmap scan report for 192.168.0.97
Nmap scan report for 192.168.0.98
Nmap scan report for 192.168.0.99
Nmap scan report for 192.168.0.100
Nmap scan report for 192.168.0.101
Nmap scan report for 192.168.0.102
Nmap scan report for 192.168.0.103
Nmap scan report for 192.168.0.104
Nmap scan report for 192.168.0.105
Nmap scan report for 192.168.0.106
Nmap scan report for 192.168.0.107
Nmap scan report for 192.168.0.108
Nmap scan report for 192.168.0.109
Nmap scan report for 192.168.0.110
Nmap scan report for 192.168.0.111
Nmap scan report for 192.168.0.112
Nmap scan report for 192.168.0.113
Nmap scan report for 192.168.0.114
Nmap scan report for 192.168.0.115
Nmap scan report for 192.168.0.116
Nmap scan report for 192.168.0.117
Nmap scan report for 192.168.0.118
Nmap scan report for 192.168.0.119
Nmap scan report for 192.168.0.120
Nmap scan report for 192.168.0.121
Nmap scan report for 192.168.0.122
Nmap scan report for 192.168.0.123
Nmap scan report for 192.168.0.124
Nmap scan report for 192.168.0.125
Nmap scan report for 192.168.0.126
Nmap scan report for 192.168.0.127
Nmap scan report for 192.168.0.128
Nmap scan report for 192.168.0.129
Nmap scan report for 192.168.0.130
Nmap scan report for 192.168.0.131
Nmap scan report for 192.168.0.132
Nmap scan report for android-642f8f214fa8b12b (192.168.0.133)
Nmap scan report for 192.168.0.134
Nmap scan report for 192.168.0.135
Nmap scan report for 192.168.0.136
Nmap scan report for 192.168.0.137
Nmap scan report for 192.168.0.138
Nmap scan report for 192.168.0.139
Nmap scan report for 192.168.0.140
Nmap scan report for 192.168.0.141
Nmap scan report for 192.168.0.142
Nmap scan report for 192.168.0.143
Nmap scan report for 192.168.0.144
Nmap scan report for 192.168.0.145
Nmap scan report for 192.168.0.146
Nmap scan report for 192.168.0.147
Nmap scan report for 192.168.0.148
Nmap scan report for 192.168.0.149
Nmap scan report for 192.168.0.150
Nmap scan report for 192.168.0.151
Nmap scan report for 192.168.0.152
Nmap scan report for 192.168.0.153
Nmap scan report for 192.168.0.154
Nmap scan report for UNKNOWN (192.168.0.155)
Nmap scan report for 192.168.0.156
Nmap scan report for 192.168.0.157
Nmap scan report for 192.168.0.158
Nmap scan report for 192.168.0.159
Nmap scan report for 192.168.0.160
Nmap scan report for 192.168.0.161
Nmap scan report for 192.168.0.162
Nmap scan report for 192.168.0.163
Nmap scan report for 192.168.0.164
Nmap scan report for 192.168.0.165
Nmap scan report for 192.168.0.166
Nmap scan report for 192.168.0.167
Nmap scan report for 192.168.0.168
Nmap scan report for 192.168.0.169
Nmap scan report for 192.168.0.170
Nmap scan report for 192.168.0.171
Nmap scan report for 192.168.0.172
Nmap scan report for 192.168.0.173
Nmap scan report for 192.168.0.174
Nmap scan report for 192.168.0.175
Nmap scan report for 192.168.0.176
Nmap scan report for 192.168.0.177
Nmap scan report for 192.168.0.178
Nmap scan report for 192.168.0.179
Nmap scan report for 192.168.0.180
Nmap scan report for 192.168.0.181
Nmap scan report for 192.168.0.182
Nmap scan report for 192.168.0.183
Nmap scan report for 192.168.0.184
Nmap scan report for 192.168.0.185
Nmap scan report for 192.168.0.186
Nmap scan report for 192.168.0.187
Nmap scan report for 192.168.0.188
Nmap scan report for 192.168.0.189
Nmap scan report for 192.168.0.190
Nmap scan report for 192.168.0.191
Nmap scan report for 192.168.0.192
Nmap scan report for 192.168.0.193
Nmap scan report for 192.168.0.194
Nmap scan report for 192.168.0.195
Nmap scan report for 192.168.0.196
Nmap scan report for 192.168.0.197
Nmap scan report for 192.168.0.198
Nmap scan report for 192.168.0.199
Nmap scan report for 192.168.0.200
Nmap scan report for 192.168.0.201
Nmap scan report for 192.168.0.202
Nmap scan report for 192.168.0.203
Nmap scan report for 192.168.0.204
Nmap scan report for 192.168.0.205
Nmap scan report for 192.168.0.206
Nmap scan report for 192.168.0.207
Nmap scan report for 192.168.0.208
Nmap scan report for 192.168.0.209
Nmap scan report for 192.168.0.210
Nmap scan report for 192.168.0.211
Nmap scan report for 192.168.0.212
Nmap scan report for 192.168.0.213
Nmap scan report for 192.168.0.214
Nmap scan report for 192.168.0.215
Nmap scan report for 192.168.0.216
Nmap scan report for 192.168.0.217
Nmap scan report for 192.168.0.218
Nmap scan report for 192.168.0.219
Nmap scan report for 192.168.0.220
Nmap scan report for 192.168.0.221
Nmap scan report for 192.168.0.222
Nmap scan report for 192.168.0.223
Nmap scan report for 192.168.0.224
Nmap scan report for 192.168.0.225
Nmap scan report for 192.168.0.226
Nmap scan report for 192.168.0.227
Nmap scan report for 192.168.0.228
Nmap scan report for 192.168.0.229
Nmap scan report for 192.168.0.230
Nmap scan report for 192.168.0.231
Nmap scan report for 192.168.0.232
Nmap scan report for 192.168.0.233
Nmap scan report for 192.168.0.234
Nmap scan report for 192.168.0.235
Nmap scan report for 192.168.0.236
Nmap scan report for 192.168.0.237
Nmap scan report for 192.168.0.238
Nmap scan report for 192.168.0.239
Nmap scan report for 192.168.0.240
Nmap scan report for 192.168.0.241
Nmap scan report for 192.168.0.242
Nmap scan report for 192.168.0.243
Nmap scan report for 192.168.0.244
Nmap scan report for 192.168.0.245
Nmap scan report for 192.168.0.246
Nmap scan report for 192.168.0.247
Nmap scan report for 192.168.0.248
Nmap scan report for 192.168.0.249
Nmap scan report for 192.168.0.250
Nmap scan report for 192.168.0.251
Nmap scan report for 192.168.0.252
Nmap scan report for 192.168.0.253
Nmap scan report for 192.168.0.254
Nmap scan report for 192.168.0.255
Nmap done: 256 IP addresses (0 hosts up) scanned in 4.38 seconds
```

As you can see, the line for 192.168.0.155 says UNKNOWN... Yet I even have Samba set up.

Can anyone help?!

---

