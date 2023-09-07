# azure-security-kv-jca-fork
This is a fork of the azure-security-kv-jca in the azure-sdk-for-java repo, to make the build and install easier.

## The original repo

https://github.com/Azure/azure-sdk-for-java/blob/main/LICENSE.txt

## How to build
```bash
cd azure-security-keyvault-jca
mvn clean package
```

## Sign Jar

jarsigner \
-keystore NONE \
-storetype AzureKeyVault \
-signedjar signerjar.jar jar-to-sign.jar "your-cert" \
-verbose \
-storepass "" \
-sigalg SHA512withRSA \
-providerPath /path/to/azure-security-keyvault-jca-2.8.0-beta.1.jar \
-providerName AzureKeyVault \
-providerClass com.azure.security.keyvault.jca.KeyVaultJcaProvider \
-J'-Dazure.keyvault.uri=https://xxx.vault.azure.net/' \
-J'-Dazure.keyvault.tenant-id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' \
-J'-Dazure.keyvault.client-id=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' \
-J'-Dazure.keyvault.client-secret=your-client-secret'

## How to run the JarSigner programmatically

The `JarSigner` is a JDK class, not a JRE class, so the sample source code was commented out in the project. To run the sample code, you can uncomment the `azure-security-keyvault-jca/src/samples/java/com/azure/security/keyvault/jca/JarSignerSample.java`, and then run it in your IDE. 
