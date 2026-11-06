# Asistente de trofeos por WhatsApp — propuesta y demo

## Resumen

Esta idea busca ayudar a un negocio de trofeos y premios a atender consultas frecuentes, recopilar los datos iniciales de una cotización y pasar la conversación a una persona cuando haga falta. El objetivo es que el equipo reciba una consulta más organizada, no reemplazar la atención humana.

El archivo [`trophy-whatsapp-demo.html`](../trophy-whatsapp-demo.html) es un prototipo interactivo en español para explicar y probar ese recorrido. Se puede compartir como demostración de la experiencia; **no es un bot conectado a WhatsApp ni una integración lista para producción**.

## Problema e hipótesis

- **Problema:** las consultas de productos, cotizaciones y pedidos pueden llegar sin la información necesaria para responder con rapidez.
- **Hipótesis:** un primer recorrido guiado puede recoger el contexto básico y facilitar la continuación con el equipo.
- **Resultado esperado:** menos preguntas repetidas y una transferencia más clara entre la automatización y el personal.
- **Principio de experiencia:** la persona debe poder pedir ayuda humana y no debe recibir promesas de precio, disponibilidad o entrega que el equipo no haya confirmado.

## Qué incluye la demo

La demo se ejecuta en el navegador y no requiere instalación:

1. Abrir `trophy-whatsapp-demo.html` en un navegador moderno.
2. Elegir un tipo de premio, consultar estilos, preguntar por un pedido o pedir atención personal.
3. Para una cotización, compartir el tipo de premio (si aplica), evento, cantidad aproximada, fecha requerida y personalización.
4. Para una consulta de pedido, introducir un número de pedido. La demo no consulta el pedido.
5. Descargar los datos introducidos en un archivo CSV o reiniciar la conversación.

El prototipo utiliza HTML, CSS y JavaScript en un único archivo, no usa dependencias externas y no persiste el estado entre recargas. El CSV se genera localmente en el navegador. Los botones de derivación solo muestran un mensaje: **no envían la conversación ni el CSV a ningún empleado**.

## Qué no incluye

- Conexión con WhatsApp, WhatsApp Business Platform o una bandeja compartida.
- Servidor, base de datos, autenticación, envío de mensajes o consulta de pedidos.
- Respuestas comerciales verificadas, precios, catálogo, inventario ni plazos.
- Transferencia real a un agente, registro de conversaciones, analítica o notificaciones.
- Persistencia: al recargar la página se pierde la conversación.

Por tanto, el prototipo no debe usarse para atender clientes reales ni para introducir información sensible.

## Recorrido propuesto

### Cotización

`Elegir producto → evento u ocasión → cantidad → fecha aproximada → grabado/diseño → revisar datos → continuar con una persona`

La opción “Otros” pregunta primero qué tipo de premio busca la persona. “Ver estilos de trofeos” ofrece continuar a una cotización o hablar con el equipo.

### Consulta de pedido

`Elegir “Consultar un pedido” → introducir número de pedido → avisar que la demo no puede consultar el estado → ofrecer continuar con el equipo`

No se deben pedir datos de pago por el chat.

### Atención humana

La persona puede elegir la opción de atención al cliente o escribir “persona”, “humano”, “agente” o “representante”. En producción, este paso debe crear una transferencia real y confirmar claramente si el equipo está disponible o cuándo responderá.

## Ejecución y colaboración

No hay proceso de compilación ni dependencias que instalar. Para probarlo, abre `trophy-whatsapp-demo.html` directamente en el navegador. Para colaborar, crea una rama por cambio, describe el comportamiento esperado en el pull request y prueba los recorridos de cotización, pedido, atención humana, descarga CSV y reinicio en escritorio y móvil.

### Archivos actuales

- `trophy-whatsapp-demo.html`: interfaz, estilos, estados de conversación y exportación CSV del prototipo.
- `README/README.md`: contexto de la idea, alcance actual y guía de trabajo para el equipo.

## Próximas decisiones y trabajo

Antes de construir la integración, el equipo debe acordar:

1. **Negocio y contenido:** nombre y catálogo definitivos; preguntas obligatorias/opcionales; respuestas frecuentes aprobadas; idiomas y tono.
2. **Cotizaciones:** datos mínimos, validaciones, reglas de urgencia y qué información necesita ventas para responder.
3. **Pedidos:** sistema de origen, método seguro de consulta y qué comprobaciones de identidad hacen falta antes de revelar información.
4. **Atención:** bandeja o CRM, horario, responsables, tiempo de respuesta esperado, tratamiento fuera de horario y recuperación ante fallos.
5. **WhatsApp:** proveedor y configuración oficial de WhatsApp Business Platform, número, plantillas cuando correspondan, consentimiento y proceso de opt-out.
6. **Datos y cumplimiento:** aviso de privacidad, finalidad, acceso por roles, retención y eliminación, región de almacenamiento y obligaciones legales aplicables.
7. **Operación:** responsable del contenido, revisión periódica, métricas útiles y procedimiento de escalado si la automatización falla.

### Etapas sugeridas

- [ ] Validar el recorrido y el contenido con atención al cliente y ventas.
- [ ] Definir requisitos funcionales, privacidad, seguridad y criterios de aceptación.
- [ ] Diseñar la arquitectura de integración con la plataforma oficial y la bandeja del equipo.
- [ ] Implementar backend, webhooks, almacenamiento mínimo necesario y transferencia a agentes.
- [ ] Probar consentimiento, opt-out, errores, duplicados, límites, privacidad y recuperación antes del piloto.
- [ ] Ejecutar un piloto controlado con métricas y responsables de soporte definidos.
- [ ] Revisar resultados y aprobar el lanzamiento antes de atender tráfico general.

## Criterios mínimos para un piloto

- El usuario puede llegar a una persona desde cada recorrido y recibe una confirmación honesta.
- Los datos enviados al equipo son legibles, pertinentes y no se duplican al reintentar.
- La consulta de pedido solo revela datos tras aplicar las verificaciones acordadas.
- Se informa al usuario del uso de sus datos y se implementan consentimiento y opt-out conforme a las reglas aplicables.
- Los mensajes, fallos y conversaciones se gestionan con permisos, retención y eliminación definidos.
- El equipo puede atender o escalar conversaciones fuera de las respuestas automatizadas.
- Se han probado en móvil los recorridos principales y los casos de error.

## Límites de privacidad para la demo

La demo actual corre en el dispositivo y no envía los datos a un servidor, pero cualquier dato introducido puede permanecer visible en la página o en el archivo CSV descargado. Usa únicamente datos ficticios durante las pruebas. No compartas números de pedido reales, datos personales ni información de pago en capturas, issues o pull requests. Antes de una integración real, el equipo debe aprobar el tratamiento y la protección de datos.
