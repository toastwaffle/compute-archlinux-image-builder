## Arch Linux Image Builder for GCE

This project provides a script that creates an Arch Linux OS image that can run
on [Google Compute Engine](https://cloud.google.com/compute/).

The image is configured to be as close as possible to a base Arch-Linux install,
but with Compute Engine features working.  Notable choices made and differences
compared to a standard Arch-Linux installation are the following:

- GRUB is used with BIOS-based boot and a GPT partition table.
- Root filesystem is ext4.
- Network is configured through dhclient.
- Rng-tools are installed and enabled to provide entropy.
- An OpenSSH server is installed and enabled, with root login and password
  authentication forbidden.
- Sudo is installed.
- [Linux Guest Environment for Google Compute
  Engine](https://github.com/GoogleCloudPlatform/compute-image-packages) is
  installed and enabled.
- Root partition and filesystem are automatically extended at boot using
  [growpart](https://launchpad.net/cloud-utils), to support dynamic disk
  resizing.
- An additional Pacman repository is used to install and keep the Linux Guest
  Environment and growpart packages up to date.


## Prebuilt Images

You can use [Cloud SDK](https://cloud.google.com/sdk/) to create instances with
the latest prebuilt Arch-Linux image.  To do that follow the SDK installation
procedure, and then run the following command:

```
gcloud compute instances create INSTANCE_NAME \
  --image-project=arch-linux-gce --image-family=arch
```


## Contributing Changes

* See [CONTRIB.md](CONTRIB.md)


## Licensing

All files in this repository are under the [Apache License, Version
2.0](LICENSE) unless noted otherwise.


## Support

Google Inc. does not provide any support, guarantees, or warranty for this
project or the images provided.
