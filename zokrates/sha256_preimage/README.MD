# Proving knowledge of a sha256 hash preimage

Goal: proving knowledge of the preimage for a given hash, without revealing what the preimage is.

In the directory of this file:

- Compile the program `zokrates compile -i sha256.zok`
- Create a witness `zokrates setup`. This command abstracts away: `--backend` which is `ark` by default, `--proving-scheme` which is `groth16` by default
- `zokrates export-verifier` to export the verifier Solidity smart contract
- `zokrates compute-witness -a 0 0 0 5`
- `zokrates generate-proof`
- ZoKrates creates a file, proof.json, consisting of the three elliptic curve points that make up the zkSNARKs proof.
- Verify proof by calling `verifyTx` function in the generated `verifier.sol` contract with parameters, e.g. :<br>

```json
[
  [
    "0x15de15ad6ee47c23efc4b57d31db485326a39ae508185d8396a41c2923be18d7",
    "0x13d16cbd5022a278cde7b510b6418f4411d0f6b5f862a4d9b07df1e103b20753"
  ],
  [
    [
      "0x1134c2924035ee9b53db9801221bc4ff70827b5aaa8d572dd864dda54b725f6a",
      "0x2d91d12d136d06d91c786b5903c205156ebabe183b3445a269aafecefd08c4e7"
    ],
    [
      "0x117563f4f742a10cd9f8ef5448c10d5f143339d50e9775f64c8a42b24de59986",
      "0x0866b9c54c69b2e673b91f81bd445b5cf1f782960114d069577e6f63e4667de4"
    ]
  ],
  [
    "0x229db1fe09d3b9235add042e0aeb0d2cc2ca1b320e560c3a77316ef01e0af36c",
    "0x1d7f2ad4254a41fbe05bc23b30e7365b732c5d937e5c2b11d24fd3a3795502a9"
  ]
]
```
