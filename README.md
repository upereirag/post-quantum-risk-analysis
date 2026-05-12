# Post-Quantum Risk Analysis

## Research Question

What is the performance cost of transitioning from classical RSA to
post-quantum ML-KEM (Kyber) cryptography, and how vulnerable are
today's systems against a quantum-capable adversary?

## Motivation

RSA — the most widely deployed asymmetric cryptosystem — is mathematically
vulnerable to Shor's Algorithm on quantum computers. This project quantifies
that vulnerability and benchmarks post-quantum alternatives.

## Findings

### RSA Decryption Growth Coefficient

| Transition          | Key Ratio | Time Ratio | Growth Coefficient |
| ------------------- | --------- | ---------- | ------------------ |
| RSA-1024 → RSA-2048 | 2x        | 1.58x      | 0.79               |
| RSA-2048 → RSA-4096 | 2x        | 4.03x      | 2.02               |

Doubling RSA key size does **not** double decryption time — growth is superlinear,
making key-size scaling an unsustainable defense against quantum threats.

### Kyber (ML-KEM) Performance

| Variant   | Public Key | Ciphertext | Keygen  | Encaps  | Decaps  |
| --------- | ---------- | ---------- | ------- | ------- | ------- |
| Kyber512  | 800B       | 768B       | 0.0058s | 0.0054s | 0.0061s |
| Kyber768  | 1184B      | 1088B      | 0.0083s | 0.0058s | 0.0155s |
| Kyber1024 | 1568B      | 1568B      | 0.0100s | 0.0047s | 0.0058s |

## Conclusion

Post-quantum migration via ML-KEM is computationally viable today.
The performance overhead is acceptable; the security gain is necessary.

## Tech Stack

Python 3.14 · cryptography · kyber-py · pandas · matplotlib

## Author

Guilherme U Pereira  
B.S. Student — Artificial Intelligence & Blockchain and Digital Cryptography, FMU  
Cisco Cybersecurity Week 2026 — Selected Participant  
Cisco Cyber Education Program — Scholarship Holder
