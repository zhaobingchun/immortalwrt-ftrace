# ImmortalWrt x86/64 with UDP receive tracing

Manually build ImmortalWrt **v25.12.2** for **x86/64 generic EFI**, with a **32 MiB boot partition** and a **300 MiB root filesystem partition**.

The source build enables function tracing, dynamic function tracing, BTF and cgroup BPF. The workflow checks the final generated Linux kernel configuration before collecting firmware. A public package-name selection is included in the workflow; no router configuration, subscription URL, password, signing private key or backup is uploaded.

## Run

Open **Actions → Build ImmortalWrt with UDP tracing → Run workflow**. Only manual runs are enabled. The workflow does not connect to a router or install firmware.

When the build finishes, download the artifact `immortalwrt-25.12.2-x86-64-ftrace`. Artifacts expire after three days. Logs and configuration reports are also uploaded when a build step fails.

## Inspect before installation

- Check `linux-kernel.config` and `package-selection-report.txt`.
- Keep `custom-kernel-packages.tar.gz`: this kernel needs modules built with its own configuration. Official prebuilt kernel modules may not match.
- Honk and its third-party LuCI packages are restored separately; this workflow does not embed private router data or Lucky configuration.
- Review the firmware partition layout and prepare a current configuration backup before installation. Devices with an existing extroot need a separate migration/restore procedure.

## References

- [ImmortalWrt source](https://github.com/immortalwrt/immortalwrt/tree/v25.12.2)
- [Honk kernel requirements](https://github.com/daeuniverse/honk/blob/main/doc/zh/how-to-start.md#linux-内核要求)
