# <img src="https://user-images.githubusercontent.com/1423657/57624925-31f08780-7593-11e9-9e1e-2f876efa23ac.png" width=300 alt="sbcOS">

**SBC-OS** is an open-source drop-in replacement for many existing commercial Session Border Controllers designed for performance and resource optimization

### Features
 
1. NAT fix including NAT ping
2. SIP analyze and normalizing (SIP/VoIP Firewall) 
3. PIKE - limits (selfilter)
4. Topology hiding
5. Header manipulation
6. SIP TLS -> SIP
7. RTP Relay (kernel space) including QOS. Amazing performance. Around 10K CC on
1U server like DELL R360.
8. RTP transcoding, RTP Recording  (user space)
9. SRTP->RTP and vice-versa
10. WebRTC and IMS support including diameter.
11. IP Trunking / Registration Trunking
12. Monitoring and statistics including RTP/RTCP MOS/QOS (Homer/Hepic)
13. Internal statistics / CPU/Memory/Network usage
14. Full IPv4 IPv6 support. 

### Optional Features
NB! For the (Lawful Interception) LI, please contact info@qxip.net

### Deployment
#### USB Stick
for everybody who has got a USB stick on KW 2019: the SBC-OS has been
installed already. You can boot your server or laptop using this stick
```
user: root
password: plusnet

```

enjoy!

#### DIY
In the repository you will find an ISO directory that contains the files to generate an ISO image, 
so just go there and run a shell script inside and to generate an ISO image or copy the data 
to your USB stick and go to sbc/boot and run bootinst.sh. The script will make your USB stick bootable. 
Dont forget to install genisoimage!


How to build the system manualy:

The system requires Ubuntu 18 or Debian 9!

Required packages (Debian 9 / Ubuntu 18)

```
apt-get install whois dirmngr multistrap reprepro binutils squashfs-tools genisoimage make linux-headers-$(uname -r) zip aufs-dkms aufs-tools aufs-dev
```

make sure you have key trusted.gpg on this directory /etc/apt/trusted.gpg if not or there's problem with you key please run :

```
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```

clone the repository, go to SbcOS and run:

```
./build_rootfs.sh
```

dont forget to install: multistrap, reprepo, whois (mkpasswd), genisoimage

The script will create a rootfs squashfs image.

After go to root directory and run script:

```
./build

```

it will generate two directories in your /tmp:
sbc-data-XXXX
sbc-initrfs-XXXX

and two scripts: that make an ISO image for you 


Important! Please be sure that your /vmlinuz is pointing to the same version of kernel
that runs now!

```
root@linux:sbcOS# uname -r
4.9.0-8-amd64
root@inux:sbcOS# ls -l /vmlinuz
lrwxrwxrwx 1 root root 26 May  5 23:20 /vmlinuz -> boot/vmlinuz-4.9.0-8-amd64

```

If you have any question, dont hesistate contact us!

Thanks Tomas M. <http://www.linux-live.org> for initramfs scripts!

