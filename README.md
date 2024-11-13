### Tar FFI

Experimental call tar native library using Bun.

Usage:

```ts
import { FFIType, dlopen, suffix } from "bun:ffi";

const lib = dlopen("target/release/libtar." + suffix, {
	compress_dir: {
		args: [FFIType.pointer, FFIType.pointer],
		returns: FFIType.u8
	}
});
const done = !!lib.symbols.compress_dir(Buffer.from("target path" + "\0", "utf-8"), Buffer.from("output path" + "\0", "utf-8"));
if (done) {
	console.log("OK");
} else {
	console.error("ERROR");
}
```
